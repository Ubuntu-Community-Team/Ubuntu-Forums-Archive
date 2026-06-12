---
title: "updation of locate database"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by resistantgnome on 2008-09-07
1) When does the database of locate command gets updated?
2) Do I ever need to change the update time of database?
3) If yes, the how?
4) Why do I need a find command when I can search things faster with locate command? Is there any other benefit of find command?

---

### Post by forger on 2008-09-07
1-3. ```
man locate
```
> 
DESCRIPTION
       locate  reads  one or more databases prepared by updatedb( 8 ) and writes file names matching at least one of the PATTERNs  to  standard  output, one per line.
```
man updatedb
```
> DESCRIPTION
       updatedb  creates  or  updates  a  database  used by locate(1).  If the database already exists, its data is reused to avoid rereading directories that have not changed.
       **updatedb  is  usually  run daily**  by  cron( 8 )  to  update  the default database.

So to update it, all you have to do is:
```
sudo updatedb
```

4. I don't know if it's faster than locate, but **find** can help you find something specific in a specific directory, recursive or not (-depth) and so on..
To see how to use it you'll have to read the manual with the list of command arguments/operators:
```
man find
```

---

