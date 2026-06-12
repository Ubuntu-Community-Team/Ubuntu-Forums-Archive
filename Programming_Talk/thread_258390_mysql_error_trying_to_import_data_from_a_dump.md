---
title: "mysql error trying to import data from a dump"
date: 2006-09-15
forum: Programming Talk
---

### Post by oldmanstan on 2006-09-15
ok, i have a dumpfile from a database, i'm trying to import it using

mysql -u <username> -p <password> < dumpfile.sql

this seems to be the accepted syntax, however, i keep getting an error 1007: Can't create database '<database>'; database exists

i saw a post that suggested dropping the database then importing, if i do that then i get an error 1049: unknown database

what the heck?! anybody got any suggestions? or maybe a different way to do it?

thanks

ps i'm using mysql v.5 from the repositories

---

### Post by gmclachl on 2006-09-16
Have you tried specifing the database you wish to use 


  mysql -u <username> -p <password> -d <databasename> < file.sql

---

### Post by ifokkema on 2006-09-16
What's in the .sql file? A CREATE DATABASE? A USE DATABASE?
- A CREATE DATABASE will not work, if the database exists. That's the first error you see. You might want to consider to either drop that line from the .sql file, or drop the database before inserting the .sql file.
- A USE DATABASE (like USE mysql) selects the next queries to run in a certain database. If that database doesn't exist, the script is whining. I guess that's the second error.

---

### Post by oldmanstan on 2006-09-17
hmm, ok, i got it fixed. i looked at the .sql file and commented out the line that created the database, then i created it manually and boom, everything worked just fine. i guess it was just being finicky.

thanks for the suggestions!

---

