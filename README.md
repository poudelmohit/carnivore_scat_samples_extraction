This notebook is created to help lab members assign samples to extract each week.
Currently, our goal is to extract and amplify at least 6 samples from each polygon and season.
A polygon contains all samples lying within 5 km of each other, and we have 40 total polygons from Indiana
5 km is the average (roughly) estimated home range radius of Bobcats and Coyotes.



Here is the detailed explanation of what I have done here:

### 1. Imported Carnivore.Diet_Working.Database.xlsx from this link (downloaded on 10/9/2024); in this workbook:
	- The overall samples we have are in two different sheets: 'Database' (937 total rows) and 'Box G' (101 total rows); excluding column label at top.
	- The sample ids listed are different in two sheets, except for 11 samples, ie: 3-0-56, 3-102-1-15, 3-15-531, 3-17-382, 3-19-375, 3-NA-11-5, 3-NA-11-6, 3-NA-13-19, 3-14-          398,   4-14-323, 3-16-255.
	- These 11 sample ids are listed in both sheets.
### 2. Combined (merged) 2 sheets into single dataframe based on column names, for easier analysis; and also removed vacant and unused columns for my analysis after merging.     The columns I removed are: Freezer, EASTING, NORTHING, YEAR, TIME
### 3. On the combined dataframe (herafter combined_df), there are 1038 rows (excluding column label). However, all the samples here donot have sufficient data of interest:
	  49 rows donot have DATE of collection, 32 rows donot have long-lat values, 
	  Also, as mentioned above, here are samples with multiple entries as well.
	  I removed, rows without date of collection and long-lat values; and ended with 985 rows * 12 columns at this point
### 4. Now, I added season column based on the date of collection. [May-Sep]="warm" and [Oct-Apr]="cool".
	  At this point, combined_df have 985 rows and 14 columns (2 new columns added are: month and season)
### 5. Next, I needed to make sure which samples are extracted, and which are not.
	For this, I used sheet 'Total Successful Extraction' in Carnivore.Diet_Working.Database.xlsx.
	In this sheet, all samples listed under column 'Successful Extractions' are recorded as 'successful extractions' (158 entries)
				all samples listed under column 'All Extractions' are recorded as 'all extractions' (272 entries)
				samples present in 'all extractions' but not in 'successful extractions' are recorded as 'unsucessful extractions'
	At this point, I added a new column 'status' in the dataframe (combined_df)
### 6. Now, I needed to add 'GROUP ID' in which samples lying within 5km of each other are grouped together. To do this in Arc GIS Pro, I exported the dataframe (combined_df)
	  After processing, I have new column 'GROUP_ID', where 40 unique groups were assigned to the samples.
	I saved this new dataframe, with group-id, extraction status, and all other information as : merged_indiana_samples (985 rows and 16 columns).
### 7. In this df (merged_indiana_samples), next step is to add samples extracted by Cierra ( at this point, I am not sure if those are successful or unsuccessful samples unless 'Successful Extractions' column is updated. However, Samples extracted by her is required to be updated somehow before selecting new samples to extract. So, I created a list of all her (63) extractions (upto week6, as of now) and updated them as 'cierra_extractions'  in the 'status' column of 'merged_indiana_samples'.  At this point, the value counts of 'status' column looks like:
  	- Unextracted : 650
  	- Successfully Extracted: 157
  	- Extraction Failed: 115
  	- Cierra Extractions: 63
## Finally, I have uploaded this dataframe as new excel sheet 'updated_indiana_samples' in the original excel workbook  'Carnivore.Diet_Working.Database.xlsx'. 

	
	






