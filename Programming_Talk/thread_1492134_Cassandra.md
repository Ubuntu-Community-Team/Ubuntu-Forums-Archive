---
title: "Cassandra"
date: 2010-05-24
forum: Programming Talk
---

### Post by cosmic_cow on 2010-05-24
Hey guys. I'm sure there are some NoSQL'ers out there. I'm working an internship with a company that's working on rolling out Cassandra as their data storage/access platform, so I'm trying to learn it, and, more than anything, its organizational structure is confusing me since some things seem to overlap. (I should note that I have precious little experience with any form of networked databasing; even my SQL experience is limited). I get that it's basically a tree structure. The terminology's just weird, and some of the documentation out there is less than helpful.
So from root to leaves it's:
Keyspaces => Rows => Column Families => Super Columns => Columns 
Is that right? Basically a 5 dimensional array? data[][][][][] ?
Colin

---

### Post by cosmic_cow on 2010-05-24
Oh wait. On further reading, I realize that a "column family" is just a table. And a column family doesn't have to contain super columns; if it does, it's a Super Column Family. Which makes the structure:
Keyspace => Column Family => Rows => Columns
or
Keyspace => Super Column Family => Rows => Super Columns => Columns

Am I at least on the right track?
Colin

---

### Post by soltanis on 2010-05-24
Wow. Talk about a serious system for indexing data. Short of whatever Google uses, Cassandra sounds like the most serious way to index >9000 TB of data over distributed clusters.

I... honestly, when I read the white paper on it, I got maybe 10% of what was being said. It sounds like a big distributed hash table in all the referential and node data is replicated across a bunch of clusters. What you've said so far sounds about right though.

---

### Post by cosmic_cow on 2010-05-25
Well...yeah, that's pretty much it. It's designed to be spread across a bunch of nodes, for fast access to huge amounts of data. Facebook developed it, and other companies, including Twitter and Digg, use it. 
It's starting to come together in my brain, but that's only after several days worth of hours of reading on it. 
Colin

---

