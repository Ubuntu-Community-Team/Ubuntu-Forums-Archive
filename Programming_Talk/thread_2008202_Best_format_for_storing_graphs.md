---
title: "Best format for storing graphs"
date: 2012-06-22
forum: Programming Talk
---

### Post by debsankha on 2012-06-22
I am working on a project which involves working with [graphs]("http://en.wikipedia.org/wiki/Graph_(mathematics)") extracted from some other source. Currently we are using python's [networkx]("http://networkx.lanl.gov/") module for analysing the graph. 

I am now faced with the task of choosing a format for storing the graphs. [Pickle]("http://docs.python.org/library/pickle.html") seems to be a good choice for a purely python based solution. However we are now in the prototyping stage and there is a significant chance that we will have to switch to C++ for performance and scalability issues. 

Therefore I'd like to have my graphs stored in a format widely supported by most graph libraries to minimise the hassle to be faced by future contributors in the project. 

Could you please give me some suggestion regarding which format I should use?

---

### Post by dagoth_pie on 2012-06-22
Have you considered creating a custom format just to store all the data you'd need to recreate the graphs? I don't know how complex your graphs are, but for smaller/simpler sets of data you'd probably be able to store it in a csv file and then take a few minutes to write and importer in any language.

---

### Post by debsankha on 2012-06-22
> **dagoth_pie said:**
> Have you considered creating a custom format just to store all the data you'd need to recreate the graphs? I don't know how complex your graphs are, but for smaller/simpler sets of data you'd probably be able to store it in a csv file and then take a few minutes to write and importer in any language.

Thanks for your suggestion. Yes, I've considered it. But my graphs are basically that of the road networks of cities, and hence can be quite large. 

I am now considering using GML.

---

### Post by the_unforgiven on 2012-06-25
If you need to implement the data-structures in C++, you can consider using:
o. [Boost Graph Library]("http://www.boost.org/doc/libs/1_49_0/libs/graph/doc/index.html")
o. [LEMON]("http://en.wikipedia.org/wiki/LEMON_%28C%2B%2B_library%29")

If you need something for *drawing*, that's a different matter altogether.
In that case, [OGDF]("http://www.ogdf.net/ogdf.php?id=") might help?

---

### Post by Garyu on 2012-06-26
I'd say the answer depends entirely on your actual question. 

I would interpret your question as "what format is best for storing the image output that is displayed on the screen?", in which case I would suggest TIFF because it is widely accepted and used a lot for printing. If size is important and you don't aim to print, I guess PNG would be an option. SVG would also be a possible way, if you want it vectorized, but then sometimes there are weird things happening for example if you try to put SVG's in MS Word.

The other possible interpretation of your question, reading your text, is "what format is best for storing data (which will later be used to present graphs)?" If you want to store the data that is used to build up the graphs, it depends entirely on what your data looks like. So maybe you could give an example of your data. One excellent way, in my opinion, would be to just make a SQLite database for your dataset instead of using files. But then you would have to have data that is easy to fit in that sort of a structure. 

Check this out for an example on using both CSV files and SQLite database: [http://stackoverflow.com/questions/2887878/importing-a-csv-file-into-a-sqlite3-database-table-using-python](http://stackoverflow.com/questions/2887878/importing-a-csv-file-into-a-sqlite3-database-table-using-python)

---

### Post by debsankha on 2012-06-27
I see that a confusion has arisen about the word "graph". In my question, I used the word "graph" to mean "a collection of edge and vertices", as the wikipedia link given clearly says. My problem has nothing to do with charts or pictorial representations of data. @garyu, your suggestion of using sqlite3 is extremely relevant. My dataset is that of road networks of cities. The vertices are intersections and the edges are connecting road segments.

---

### Post by Garyu on 2012-06-27
> **debsankha said:**
> I see that a confusion has arisen about the word "graph". In my question, I used the word "graph" to mean "a collection of edge and vertices", as the wikipedia link given clearly says. My problem has nothing to do with charts or pictorial representations of data. @garyu, your suggestion of using sqlite3 is extremely relevant. My dataset is that of road networks of cities. The vertices are intersections and the edges are connecting road segments.

Yeah, OK, but what exactly is the data you want to store/transfer? A bitmap of 1/0 (or black/white if you prefer) could represent what you describe, which could be stored in a matrix, but would not be good to store in a db although TIFF would work. On the other hand, if you're working with roads you might as well use shape files (ESRI style) and get projection and everything right, which could be stored in a db (like PostgreSQL with PostGIS) or as individual files. There's like a million options in between those two, and if you want to get a good answer then you need to give a better background to your question.

---

### Post by The Cog on 2012-06-28
Garyu: Forget images - he is looking to store a data structure - a list of nodes e.g. [id,name,latitude,longditude, population] and a list of connecting links, e.g. [id,starting_node,ending_node,width,speed_limit]. Apparently mathematicians call this a graph, which I find very confusing.

debsankha: I second the idea of a csv file or an sqlite database. I think storing an entire roadmap as an "object" such as with pickle or json is potentially fragile, as one error could prevent any of the graph loading. Lists of lines or rows, one per node or edge feels much more robust to me. 

sqlite would allow you to maintain multiple tables, e.g. a table for nodes and a table for edges, and you could add other tables for supplimentary information later if you wanted. So that would probably be my recommendation.

---

