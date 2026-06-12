---
title: "PostgreSQL query start up help"
date: 2011-03-09
forum: Programming Talk
---

### Post by Xender1 on 2011-03-09
Just need some help with the initial set up of starting to make a query file using psql. 

Currently I have an .sql file which creates a bunch of tables and also fills in the tables with data.

I have this in a directory and I just need help with the command in psql to somehow use this .sql to create the database. There will be another .sql file which I query the database from. 
I know what I need to do for the commands to get the data I need, I just need help on where to start on how to use psql to make a database from a .sql that has the table and info for the tables, and then psql to read another .sql to query the database. 

Sorry this is my first time working with sql so I apologize if my explanation sounds strange.

edit: some more info is I am trying to do this on my local host and gedit to make the .sql files

---

### Post by Xender1 on 2011-03-10
Ok, so right now im working with this command:
```

psql --host=localhost -U tempusr -f set_everything_up.sql

```
which returns:
```

psql: FATAL:  password authentication failed for user "tempusr"
FATAL:  password authentication failed for user "tempusr"

```

I also edited my pg_hba.conf file to have my local line too:
```

local   all         all                               md5

```

I am so confused as to the command line args i need to give psql in order to make the data base from the tables and info from set_everything_up.sql

---

