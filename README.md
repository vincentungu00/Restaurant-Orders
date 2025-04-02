# Restaurant-Orders

This repository consists of data analytics exploration for Restaurant Orders dataset downloaded from Maven Analytics. Link to the Google Slide: [https://docs.google.com/presentation/d/1D5dHFdLmDFuCpNfCSbCJknIiJ1Z8SyvTJmszVRSedg4/edit#slide=id.p](https://docs.google.com/presentation/d/1D5dHFdLmDFuCpNfCSbCJknIiJ1Z8SyvTJmszVRSedg4/edit?usp=sharing)

## Data Engineering
From the source, I was given two tables: 
* menu_items.csv      : contains menu information, such as item name, category, and price.
* order_details.csv   : contains order information, such as order time and items.

I loaded the data into Google Colaboratory to do the data wrangling. 

In this project, the data wrangling process was:
1. Cleaning the data
2. Transforming the data
3. Creating a star schema

When I mentioned cleaning the data, it was a process of making sure that the records were not duplicated and didn't contain empty values. Fortunately, the data used in this project wasn't a big mess. 

The transforming process was the heaviest part of the data wrangling process. The transformation was done not only considering the technical perspective, but also considering how would the data model should be if I were to build the business' data model. 

1. Changed the order_details_id. \
The order_details_id started from 1. However, this number was incremental even though the order_id was different. What I imagined was each order_details_id would start from 1 for each order_id.

2. Created quantity. \
There were records with the same order_id, same item_id, but different order_details_id. This was telling me that the items in kept in this dataset was inserted per row regardless it was the same item as the previous record. Being said, I could grouped these records and calculated the duplicated item_id(s) into quantity.

3. Expanded time and date features. \
Since I would create a star schema, I had to create possible features that would be inserted into the dimension tables. 

4. Added revenue. \
Since there was no revenue feature in the dataset, I created this for the analysis purposes. I assumed that the revenue for each item was 50% from the offered price.

The final process was to create a star schema. In a star schema, I created a fact table and three dimension tables. The fact table consisted of transactional data, or I would say contain numerical records, including the id(s) to join with the dimension tables. The three dimension tables covered time dimension table, date dimension table, and menu dimension table, where each dimension table contained features that was unique to the dimension table's id (or key). 


