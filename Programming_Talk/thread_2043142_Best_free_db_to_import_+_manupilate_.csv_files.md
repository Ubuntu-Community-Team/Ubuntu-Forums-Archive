---
title: "Best free db to import + manupilate .csv files"
date: 2012-08-15
forum: Programming Talk
---

### Post by psycho5 on 2012-08-15
Hi guys,

I'm looking for a db that can help in importing and manupilating data from .csv files.

The files are quite big in size for .csv(s) (2 to 8 mb) and each file has 1000 rows. There are all in all 32-35 files. 

I need to be able to sort data and compile all files together using certain filters. Those filters would be indicated by certain column values. 

Any suggestions?

---

### Post by Some Penguin on 2012-08-15
Just about any major database is likely to have support for CSV input.

PostgreSQL is pretty decently engineered, is open-source, and has a good universe of libraries and drivers for various languages.  But just about any relational database will likely suffice; 35000 rows and well under a GB of data is nothing to worry about.

---

