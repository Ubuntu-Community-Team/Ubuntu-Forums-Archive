---
title: "dbconfig-common and dkpg-reconfigure"
date: 2010-11-23
forum: Packaging and Compiling Programs
---

### Post by gencha on 2010-11-23
I wonder what the correct procedure is to use dbconfig-common in regards to dpkg-reconfigure. My current SQL data that I supply simply creates all tables, foreign keys, etc and inserts some data. 

But when I reconfigure, my tables can't be dropped because there are foreign key relationships. 
So I am assuming at this point that I should pretty much clear the whole database at the beginning of my (/usr/share/dbconfig-common/data/) SQL file.
Is that common procedure or am I approaching this the wrong way?

---

