---
title: "Embedded db (h2) problem with jar and moving the db file and console access"
date: 2010-03-14
forum: Programming Talk
---

### Post by cdiem on 2010-03-14
I'm trying to store information to h2 ([http://www.h2database.com/](http://www.h2database.com/)) from a java app. I seem to have misunderstood something about the embedded db. Here's the problem:

- starting the h2 from console (java -jar h2.jar) and creating some tables (from the browser interface) is fine. 
- then trying to access the same tables using jdbc from the application gives me "table not found" exceptions. "show tables" returns a resultset with 0 rows. 

Also:
- creating a table programatically from the java code creates a table just fine
- then the table cannot be seen when accessing the same database from the console through the browser interface (with java -jar h2.jar).
- also when moving the location of the database to another folder, the tables are gone
- the tables are gone also when creating an executable jar, so all data i try to save into the database is gone as well. 

I'm using Eclipse for the jar generation, if that matters; I'm trying to put the db into the jar and put info in it/get info from it.
 
I have executed all the actions, taking into account the lock files (e.g., I have stopped the java app first and then tried accessing the db from console, etc).

I'm inexperienced with embedded db's; there's probably something fundamental here that I have misunderstood. I have googled for some hours, but I cannot seem to find my mistakes.

---

