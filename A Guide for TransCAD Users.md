# A Guide for TransCAD Users



- [A Guide for TransCAD Users](#a-guide-for-transcad-users)
  - [Introduction](#introduction)
  - [View the dataset](#view-the-dataset)
    - [Input data](#input-data)
      - [Node data](#node-data)
      - [Link data](#link-data)
      - [OD data](#od-data)
    - [Output data](#output-data)
      - [Traffic assignment results](#traffic-assignment-results)
      - [Travel time between OD pairs](#travel-time-between-od-pairs)
      - [Visualization](#visualization)
  - [Modify the dataset](#modify-the-dataset)
    - [Modify the road attributes](#modify-the-road-attributes)
    - [Modify the OD demand multiplier](#modify-the-od-demand-multiplier)
    - [Modify the BPR parameters](#modify-the-bpr-parameters)
    - [Modify the turn penalty parameters](#modify-the-turn-penalty-parameters)
    - [Execute a new traffic assignment](#execute-a-new-traffic-assignment)
  - [Notes](#notes)



## Introduction

This guide is provided for users who are not familiar with the commercial transportation planning software [TransCAD](https://www.caliper.com/tcovu.htm) but wish to get access to the traffic assignment dataset we presented through this software. The software version we used in this guide is 9.0 and the detailed authorization information is shown below.

![1](images/TransCAD/1.png)


## View the dataset

The traffic assignment results of TransCAD are stored in the folder corresponding to each city with a file named ‘02 TransCAD results’. We take the city of San Francisco as an example, and here below are all the results obtained from the TransCAD.

![2](images/TransCAD/2.png)

### Input data

Node data, link data, and OD data are the three main input data for traffic assignment, here we give a brief demonstration about how to view these data in TransCAD respectively.

First of all, open the software and click the open file button.

![3](images/TransCAD/3.png)

Then, navigate to the storage location of the dataset on your computer, and open the file with the ‘.dbd’ extension. It is a file format used by TransCAD to store the road network geographic information.

![4](images/TransCAD/4.png)

Then the visualization of a city’s road network would be displayed in TransCAD as below.

![5](images/TransCAD/5.png)

#### Node data

Open the node layer in the ‘Display Manager’ box by clicking the green check box and activate it in the working layer box.

![6](images/TransCAD/6.png)

Click the ‘New Dataview’ button and then the node attribute table can be retrieved.

![7](images/TransCAD/7.png)

Below is the corresponding node attribute table and each row records a node's information.

![8](images/TransCAD/8.png)

As shown in the dataview table above, the fields with a green background are automatically generated by TransCAD when importing the data, while the fields with a light-colored background contain information from the initially imported data. A detailed description of each node filed is provided below.

- ID: ID generated automatically by TransCAD
- Longitude: Longitude generated automatically by TransCAD
- Latitude: Latitude generated automatically by TransCAD
- Elevation:	Elevation generated automatically by TransCAD
- Node_ID:	Original ID information
- Lon:	Original Longitude information
- Lat: Original Latitude information
- Tract_Node: A binary variable indicating whether a node is a Traffic Analysis Zone (TAZ) or not

#### Link data

Similarly, the link attribute table can be retrieved in the same way.

![9](images/TransCAD/9.png)

Here below is the corresponding link attribute table and each row records the information of a link.

![10](images/TransCAD/10.png)

Similarly, the fields with a green background are automatically generated by TransCAD when importing the data, while the fields with a light-colored background contain information from the initially imported data. Please note that in TransCAD, a link can be either unidirectional or bidirectional. The fields containing ‘AB’ or ‘BA’ indicate the two different directions of each road segment. A detailed description of each link filed is provided below. 

- ID: ID generated automatically by TransCAD
- Dir/direction: A variable indicating whether a link is bidirectional or not (0 for bidirectional while 1 or -1 for one-way)
- Length: Length (km) generated automatically by TransCAD
- Link_ID: Original length ID information
- From_Node_ID: The node ID of the starting point of this link
- To_Node_ID: The node ID of the ending point of this link
- Capacity: The link capacity information (veh/h)
- Free_Speed: The link free flow speed information (km/h)
- Link_Type: Supported link types in osm2gmns (1 for motorway, 2 for trunk, 3 for primary, 4 for secondary, 5 for tertiary)

#### OD data

The OD data can be retrieved in the same way. Note that OD matrix tables are stored with a ‘.mtx’ extension in TransCAD.

![11](images/TransCAD/11.png)

Here below is the corresponding OD matrix table. The rows or columns record the ID of each Traffic Analysis Zone (TAZ), while each cell represents the corresponding travel demand between TAZs.

![12](images/TransCAD/12.png)

### Output data

Output data include traffic assignment results data and travel time between each OD pair.

#### Traffic assignment results

Traffic assignment results data are stored in the file called ‘LinkFlows.bin’, and it can be opened in the same way as described earlier.

![13](images/TransCAD/13.png)

Below are the corresponding traffic assignment records for each link after opening the results file.

![14](images/TransCAD/14.png)

A detailed description of the assignment results for each link is provided below. 

- ID: ID is generated automatically by TransCAD, which is the same as the link ID in the link layer
- Flow: The final assigned traffic flow (veh/h)
- Tot_Flow: Total traffic flow (veh/h) for both directions
- Time: Loaded travel time (min) for each link
- Max_Time: Maximum loaded travel time (min) for links in both directions
- VOC	Volume: to Capacity (V/C) ratio for each link
- Max_VOC: Maximum V/C ratio for links in both directions
- VKmT: Vehicle-Distance Travelled for each link
- Tot_ VKmT: Total Vehicle-Distance Travelled for both directions
- VHT: Vehicle-Hours Travelled for each link
- Tot_ VHT: Total Vehicle-Hours Travelled for both directions
- Speed: Loaded travel speed (km/h) for each link
- VDF: Loaded cost (result from the Volume Delay Function) for each link
- Max_ VDF: Maximum loaded cost for links in both directions

#### Travel time between OD pairs

The User Equilibrium (UE) conditions can be satisfied after the traffic assignment and therefore the travel time (using minutes as the unit) between each pair of the OD demand can be calculated based on the travel flow assigned on each link. Here the travel time results are presented as a matrix form which is similar to the OD demand matrix, and the value in each cell represents the shortest travel time between the corresponding origin and destination.

Open the travel time matrix named ‘ShortestPath.mtx’.

![15](images/TransCAD/15.png)

Below are the detailed contents after opening the travel time (min) matrix.

![16](images/TransCAD/16.png)

#### Visualization

First of all, we make a selection set to screen out all the connectors by clicking the ‘Select by Condition’.

![17](images/TransCAD/17.png)

Define the conditions.

![18](images/TransCAD/18.png)

Then, all the connectors are selected out and marked with the green line.

![19](images/TransCAD/19.png)

Make the connectors invisible by clicking the ‘Selection Settings’ button.

![20](images/TransCAD/20.png)

Change the status of the connectors selection set to be invisible.

![21](images/TransCAD/21.png)

Open the traffic assignment results table ‘LinkFlows.bin’ and click the ‘Join Dataviews’ button.

![22](images/TransCAD/22.png)

Join the link table (‘San Francisco_link’) and the traffic assignment results table (‘LinkFlows’) together based on the common ID field. The specific setting is shown below.

![23](images/TransCAD/23.png)

Keep all the tables opened and click the ‘Create Flow Map’ button as shown below.

![24](images/TransCAD/24.png)

Define the visualization setting in the ‘Create a Traffic Flow Map’ dialog box.

![25](images/TransCAD/25.png)

Click OK and then the visualization of the traffic assignment flow can be shown below.

![26](images/TransCAD/26.png)

## Modify the dataset

If you want to modify the parameters for traffic assignment according to your own needs and conduct different scenario testing accordingly, this section will briefly explain how to perform these operations.

### Modify the road attributes

If you want to modify the attributes of a specific type of road, you can perform a similar operation as creating the connectors selection set earlier to select roads of that specific type, and then make uniform modifications to the selected set of roads.

For example, define the select conditions for ‘expressways’.

![27](images/TransCAD/27.png)

Then all the expressways can be selected and marked with blue lines.

![28](images/TransCAD/28.png)

Open the link dataview table and identify the field you want to modify by right-clicking the mouse on the corresponding field. Then click the ‘Fill’ as shown below to make the modification.

![29](images/TransCAD/29.png)

Through this approach, you can assign a uniform value (Single Value option) to a certain type of road or assign values to that type of road based on calculations involving other fields (Formula option).

![30](images/TransCAD/30.png)

### Modify the OD demand multiplier

With the OD matrix file open, you can conduct the traffic assignment by clicking the ‘Traffic Assignment’ button demonstrated below.

![31](images/TransCAD/31.png)

You may be asked to specify a road network file with the ‘.net’ extension, which records all road attribute information used for traffic assignment. 

![32](images/TransCAD/32.png)

Then, in the popped-up ‘Traffic Assignment’ dialog box, you can specify an OD demand multiplier by changing the value of the ‘Loading Multiplier’ text box on the ‘Other Options’ page.

![33](images/TransCAD/33.png)

### Modify the BPR parameters

In the same popped-up ‘Traffic Assignment’ dialog box, you can modify the Dealy Function as well as the corresponding parameters.

![34](images/TransCAD/34.png)

### Modify the turn penalty parameters

Similarly, you can modify the turn penalty parameters by clicking the ‘Network’ button as shown below. Choose the ‘Turn’ as the Penalties mode on the ‘general’ page.

![35](images/TransCAD/35.png)

Then, you can specify the detailed turn penalty parameters in the following ‘Network Setting’ dialog box.

![36](images/TransCAD/36.png)

### Execute a new traffic assignment

After defining all the parameters and specifying the store location for the final results, you can then conduct a new traffic assignment. The output files include a traffic flow table (‘LinkFlows’) as described above and a report file containing the iteration information of the optimization algorithm (‘IterationLog’).

![37](images/TransCAD/37.png)

After the traffic assignment, a visual interface of traffic flow will be automatically generated. You can save this interface setting as a project file with the ‘.map’ extension for direct opening in the future.

## Notes

For users who are unable to use the TransCAD software, we have exported the traffic assignment results in the same folder as CSV files to facilitate their usage. Specifically, the file named ‘LinkFlows.csv’ corresponds to ‘LinkFlows.bin’ in TransCAD representing the final traffic assignment results, while the file named ‘ue_travel_time.csv’ corresponds to ‘ShortestPaths.mtx’ in TransCAD representing the travel time (min) between TAZs.

![38](images/TransCAD/38.png)