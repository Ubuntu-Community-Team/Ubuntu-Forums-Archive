---
title: "Primary keys in MySQL database - numbers or strings better?"
date: 2011-11-11
forum: Programming Talk
---

### Post by Mezzoforte on 2011-11-11
The other day I created a database table in MySQL, and first I made it so that there are two columns, the first column holding a unique id, and the second holding a category name.

First I let the id column be the primary key, and associated entries in another database table with this value. But then I thought, maybe it's unnecessary to have this id column, when I can just associate the category name with entries in another table. 

Let me make it a little more clear. Background setting: We have a database with 3 tables.
**Table1** stores data about news articles.
**Table2** stores all different categories an article can belong to (and an article can belong to more than one category)
**Table3** is a lookup table which says which articles are associated with which category.

In Table1 I think it's natural to keep one column for the unique id of every article. But what about Table2? In Table3 I want to store the article id and a category id or name in every row, like this:

option 1:

article_id --------------- category_id
1 --------------- 2
1 --------------- 3
2 --------------- 2

or if I choose to only store the category names in Table2 and use them as the primary key:

article_id --------------- category_name
1 --------------- world news
2 --------------- world news
2 --------------- politics


So the real question here becomes, which way would be the more efficient? Does it take longer for the database to find an entry in a primary key column consisting of a unique string of characters than a unique number id?

Apologies in advance if the dilemma is not clear enough. Hope it gets through though. And by the way, the tables are just examples, nothing I'll actually use.

---

### Post by SeijiSensei on 2011-11-11
I've used both MySQL and PostgreSQL (prefer the latter) with both numeric and string keys.  I've never seen any performance difference because of my choice of key.  I often use "Unix time" (consecutive seconds since 1/1/70) as primary keys since creating a record with the current time as a key lets me keep track of when the record was created.  (I rarely if ever use sequence numbers as a primary key.)  When privacy matters, I'll use something like a SHA1 hash as a key.

Since you're going to be joining tables on this key, make sure you construct an index on the "foreign key" in the linked table (stories in your case it appears).  Indexing matters much more for performance that the choice of numeric vs. string keys.  You might also want to look into methods for enforcing "[referential integrity]("http://teamtutorials.com/database-tutorials/referential-integrity-with-mysql")."

---

### Post by mbeach on 2011-11-11
very clear. You may actually be venturing on the bigger question with endless debate about natural vs surrogate keys.

[http://www.google.ca/search?q=database+keys+id+versus+descriptive](http://www.google.ca/search?q=database+keys+id+versus+descriptive)

If you have the time, I'd also suggest a solid reading of the Art of SQL (Stephane Faroult).
[http://books.google.ca/books?id=HfcMDvxb43AC&pg=PA114&lpg=PA114&dq=natural+keys+stephane+faroult&source=bl&ots=NB12yMMDo2&sig=KPSrvXPgCwayK57gLrjHBuhUiZ0&hl=en&ei=VMe9Tr3MIMbz0gHgpZTeBA&sa=X&oi=book_result&ct=result&resnum=1&ved=0CBsQ6AEwAA#v=onepage&q=natural%20key&f=false](http://books.google.ca/books?id=HfcMDvxb43AC&pg=PA114&lpg=PA114&dq=natural+keys+stephane+faroult&source=bl&ots=NB12yMMDo2&sig=KPSrvXPgCwayK57gLrjHBuhUiZ0&hl=en&ei=VMe9Tr3MIMbz0gHgpZTeBA&sa=X&oi=book_result&ct=result&resnum=1&ved=0CBsQ6AEwAA#v=onepage&q=natural%20key&f=false)

---

