# Analysing Video Game Sales and Clustering by Similarities

![sales by platform by region](https://user-images.githubusercontent.com/95157802/211964444-850f27d3-3d50-4d03-8887-a97c9462b0a5.PNG)

This project explores the world of video games and their sales data. Exploratory data analysis will be conducted to __identify which gaming platforms and regions have seen the most game sales__, as well as study __the sales surrounding 7th Generation Consoles__ (Nintendo Wii, PS3, Xbox360). Further, a __clustering algorithm will be trained to group video games that share similar sales characteristics__, which can in turn help game designers and publishers to understand potential patterns behind video games that see similar level of sales.

The following key questions will be answered:

1. What gaming platforms and regions have seen the most sales?
2. How have the number of games released and games sold changed over the years? 
3. Which of the competing 7th generation gaming console saw the most game releases and sales during their prime?
4. What is a suitable number of clusters for the dataset's samples? 
5. What are some of key features that inform the clustering partitions?

## This repo includes the following:

- "_Video_Game_Sales_Analysis_And_Clustering.ipynb_" - Jupyter notebook showcasing Python data pre-processing workflow of the raw CSV file, data manipulation, exploration and analysis, clustering machine learning model training and evaluation.

- "_vgsales.csv_" - Raw CSV file containing sales data of popular video games sourced from [here](https://www.kaggle.com/datasets/gregorut/videogamesales).

- "_Video Game Sales Data (Clean).csv_" - The pre-processed dataset with missing values addressed.

- "_Video Game Sales Data - Analysis.pbix_" - Power BI Desktop document for data visualization and further analysis that uses the pre-processed version of CSV file.

- "_Video Game Sales Data - Analysis.pdf_" - PDF report exported from the Power BI document.

## Insights

Below are some of the main insights and visualizations of this project, although the __Jupyter notebook is far more thorough and captures the associated code in pre-processing and manipulating the data, and training the machine learning model__:

### Insights on Relationships between Sales numbers, Region of Sales, and Gaming Platforms

![sales by region](https://user-images.githubusercontent.com/95157802/211964784-99f3ec94-3ea2-464d-b6cc-b1bf6e40001f.PNG)

![global sales df](https://user-images.githubusercontent.com/95157802/211964845-1160eca7-37d7-42fa-93d3-0138cd24b6e6.PNG)

![sales by platform by region](https://user-images.githubusercontent.com/95157802/211964803-b5fefc7f-0e8c-4d6a-9e5d-d9a780260647.PNG)

- Figure 1 shows that North America accounts for most video game sales internationally with 4.3 billion sales, followed by Europe and then Japan. All other international video game sales outside of NA, EU and JP make up for less sales than Japan alone as a country!

- The 5 platforms with the most global sales are also the top 5 platforms with the most game title releases. The PS2 is the only videogame platform with over 1 billion videogame sales, seeing 1.23 billion global sales. Comparatively, the Nintendo DS is the platform with the most videogame releases, but 5th with most sales.

- Figure 2 shows the relationship between platform sales per region and shows how The Nintendo DS is by far the most popular handheld console, while the PS2 is the most popular video game platform of all time. Competing 7th generation consoles such as the Nintendo Wii, PS3 and Xbox360 saw similar levels of game sales globally. SNES games had more sales in Japan than the rest of the world combined.

### __Insights on Relationship Between Videogame Releases, Sales and Year of Release__

![games release and games sales](https://user-images.githubusercontent.com/95157802/211965475-002504dc-aabc-43f3-a655-ff171f80ad7d.PNG)

![sales and release on 7th gen](https://user-images.githubusercontent.com/95157802/211965254-7d144641-2f5e-4261-a58c-fa009af502e7.PNG)

- Figure 3 shows the number of yearly game releases and global sales closely follow one another, seeing similar levels of proportional increase and decrease. Between 1980 and 1990, there were very few videogames releases compared to what would follow in the next decades. From 1990 up until 2008, there is a significant gradual overall increase in the number of videogames produced and global sales, with a steeper decline in the numbers of both game release and sales in the years after.

- Figures 4 and 5 show that between the 3 7th Generation consoles (Wii, PS3 and Xbox360), the Wii had the most game sales and games released in 2007, 2008 and 2009, but sees a sharp decline in both moving into the following years. The PS3 and Xbox360 had similar levels of games sales and new releases since the videogame consoles' debut, and they follow each other closely in terms of sales and new game releases.

### __Insights on Clustering Model Development__

![explained variance](https://user-images.githubusercontent.com/95157802/211965670-c5775a20-c6f1-4a11-8ed2-9e3ac17865bb.PNG)

![k-means graph](https://user-images.githubusercontent.com/95157802/211965688-9dc2db77-fa9a-44fc-a6c0-044c543501b9.PNG)

![df with components](https://user-images.githubusercontent.com/95157802/211966456-745742d2-416a-480f-a8a6-525453fd5a0b.PNG)

- The PCA model trained with the numerical data from the DataFrame shows that with __3 components explain approximately 90% of the variance__, while the remaining 3 components explain only about 10%.
- Visualing Inertia vs the Number of Clusters reveals that __the optimal number of clusters is about 4 or 5 clusters__, minimizing the inertia while maximizing the number of clusters. 4 clusters were used for the final KMeans model.

### __Insights from Clustering Visualization__

![pca components scores scatter](https://user-images.githubusercontent.com/95157802/211965933-e5c38b7e-3315-4b0c-9fe2-b07dc77476c1.PNG)

![sales hue by component pt1](https://user-images.githubusercontent.com/95157802/211966054-d53dc8da-3a10-43be-85d8-cce4a0d22a3f.PNG)
![sales hue by component pt2](https://user-images.githubusercontent.com/95157802/211966059-5dd04739-abce-4cbd-9dde-82e59bd8bdac.PNG)

![pairgrid](https://user-images.githubusercontent.com/95157802/211966136-b695fa63-da8c-42b4-a8dc-ac486fd9679d.png)

- The KMeans model generated 4 clusters. From the graphs explored it appears that the clusters corresponds to tiers in terms of sales numbers among the videogames, with the first and fourth clusters being more heavily influenced by the <code>Year!</code> variable.
- The __fourth cluster example appears to consist of the most "common" samples__ with 10,674 games, where all samples are concentrated around the lower range of sales numbers.
- The __first cluster tends to show higher sales numbers on average than the samples in the fourth cluster__ with 5,065 games, although they are fairly intermingled with the fourth cluster when visualized through a 2D plot. Interestingly, these samples also correspond to videogames that were sold primarily between 1980 and 2005.
- The __second cluster appears to consist of the outliers in the data__, which are games with extraordinary sales numbers compared to all the others. Consequently, there are only a small fraction of all games here with 34 games.
- Finally, the __third cluster consists of games which generally have a higher number of sales__, but not as high as the second cluster.
- The most extreme outlier value visible in several of the plots produced corresponds to "Wii Sports" a game that came with the Nintendo Wii console. If K-means was instantiated with 5 clusters instead of 4, it would have classified Wii Sports in a cluster of its own by itself.


## __Conclusion__

This exploration of videogame sales data through data manipulation and visualization has allowed for a deeper understanding around the magnitude of games sales, count of new videogame titles and how these compare between different regions and platforms. In addition, plotting these over time, and with a focus on the 7th generation consoles, allows for a comparative sales analysis over the years and between different competing videogame publishers.

The __clustering analysis could be beneficial for game designers and publishers to maximize sales__, as they can look further into games that were classified in the second and third clusters and were published recently, as these appear to consist of the latest "best sellers" out of all the videogames. By studying attributes of these games such as the games' titles, genre and platform, as well as other characteristics not captured in this dataset, such as the game's design and their marketing campaigns, patterns can be identified to help design and publish future successful games.
