

# Leila Readme



# Step-by-Step Guide to Creating Network Visualizations in Gephi

## Introduction

This guide will help you import and visualize network data in Gephi using the example of Individuals.csv (nodes) and Edges.csv (edge connections). It's designed for people who understand basic network concepts but need practical help with Gephi's specific requirements.

## Preparing Your Data Files

Gephi has strict naming requirements for your CSV files:

### For Nodes CSV (Individuals.csv):

- Rename the "UID" column to **"Id"** (with capital I, lowercase d)
- Keep other columns as they are ("Name", "Alt Names", "Birthdate", "Place of Birth", "Death", "Source")
- Make sure the Id values match exactly what's referenced in your edges file

### For Edges CSV (Edges.csv):

- Rename "Person_1" to **"Source"**
- Rename "Person_2" to **"Target"**
- Rename "Relationship_Type" to "Type" (optional but recommended)
- Make sure the "Source" and "Target" values match the "Id" values in your Individuals.csv file

## Importing Your Network Data

### Step 1: Start a New Project

1. Open Gephi
2. Click on "New Project" from the start screen

### Step 2: Import Nodes First

1. Go to File > Import Spreadsheet
2. Browse to your modified Individuals.csv file
3. In the import settings:
   - Set "Import as" to "Nodes table"
   - Make sure "Separator" is set to "Comma"
   - Check the preview to ensure data appears correctly with "Id", "Name", etc.
4. Click "Next"
5. In the data type dialog:
   - Make sure "Id" is set as "Integer" (since UIDs are numbers)
   - Set "Name" as "String"
   - Set "Alt Names" as "String"
   - Set "Birthdate" as "Double"
   - Set "Place of Birth" as "String"
   - Set "Death" as "Double"
   - Set "Source" as "String"
6. Click "Finish"
7. When asked "Do you want to create a new workspace?", select "New workspace"
8. Click "OK"

### Step 3: Import Edges

1. Go to File > Import Spreadsheet
2. Browse to your modified Edges.csv file
3. In the import settings:
   - Set "Import as" to "Edges table"
   - Set "Separator" to "Comma"
4. Click "Next"
5. Set data types:
   - Make sure "Source" is set as "Integer"
   - Make sure "Target" is set as "Integer"
   - Set "Type" as "String"
   - Set "UID" as "Integer"
6. Click "Finish"
7. **CRITICAL STEP**: When asked about the workspace, select "**Append to existing workspace**" (NOT the default option)
8. Click "OK"

## Visualizing Your Network

### Step 4: Apply a Layout

1. Go to the "Overview" tab if not already there
2. In the Layout panel (left side):
   - Choose "ForceAtlas 2" layout algorithm
   - Click "Run"
   - Let it run for a minute or so until the network stabilizes
   - Click "Stop" when satisfied

### Step 5: Show Node Labels

1. In the bottom panel, find the "Labels" section
2. Check the "Show labels" checkbox
3. From the "Text" dropdown, select "Name" (the person's name from your Individuals.csv)
4. Adjust label size to about 1.2 or 1.5 for better readability

### Step 6: Format Nodes and Edges

1. Go to the Appearance panel (top-left)
2. To change node colors:
   - Select "Nodes" > "Color" tab
   - Choose "Partition"
   - Select "Place of Birth" to color nodes by their birthplace
   - Click "Apply"
3. To change node shapes:
   - Select "Nodes" > "Shape" tab
   - Choose your preferred shape (like Diamond)
   - Click "Apply"
4. To change edge colors by relationship type:
   - Select "Edges" at the top of Appearance panel
   - Select the "Color" tab
   - Choose "Partition"
   - Select "Type" from the dropdown
   - Assign different colors to different relationship types (like red for "parent", blue for "spouse")
   - Click "Apply"

### Step 7: Remove Isolated Nodes (Nodes Without Connections)

1. Go to the Filters panel (right side)
2. Expand "Topology" filters
3. Drag "Degree Range" to the Queries area
4. Set minimum degree to 1 (to keep only connected individuals)
5. Click "Apply"

### Step 8: Adjust Label Positions

1. In the Labels panel (bottom):
   - Adjust font size to 1.2
   - Set color to black for better contrast
2. Use Label Adjust layout:
   - In Layout panel, select "Label Adjust"
   - Set "Node-Label Distance" to 10
   - Click "Run"
   - Click "Stop" after a few seconds

### Step 9: Create Final Visualization

1. Go to "Preview" tab when ready
2. Adjust settings for final appearance:
   - Under Node Labels, select "Show Labels"
   - Set "Font" to a readable size
   - Set "Color" to black
   - Under Edges, adjust thickness to 1.0
3. Click "Refresh" to update the preview

### Step 10: Export Your Visualization

1. In Preview tab, click "Export"
2. Choose format (PDF recommended for best quality)
3. Set resolution and size
4. Click "OK" and save as "Individual_Relationships_Network.pdf"

## Common Issues and Solutions

- **Nodes and edges not connecting**: Make sure Id values in Individuals.csv exactly match Source/Target values in Edges.csv
- **Labels not showing**: Verify that the "Name" column exists and "Show labels" is checked
- **Relationship types not appearing**: Check that "Relationship_Type" was properly renamed to "Type" and imported correctly
- **Birthdate/Death dates not formatting properly**: These should be imported as Double data type
- **Only seeing some individuals**: If you filtered by degree, some individuals without connections won't appear

Remember to save your project frequently using File > Save as "Individuals_Network.gephi".

