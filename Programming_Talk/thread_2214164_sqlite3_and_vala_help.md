---
title: "sqlite3 and vala help"
date: 2014-03-30
forum: Programming Talk
---

### Post by littledaisyphysics on 2014-03-30
Could someone take a look at my code? I'm currently learning how to use Vala and sqlite3, and I'm experiencing a problem where a table cannot be located within the database.

The database does have a table within it called "Constants", and it does have data within it so I definitely must be accessing it wrong.


[ATTACH=CONFIG]251598[/ATTACH]

Thanks.

---

### Post by spjackson on 2014-03-31
Welcome to the forums.

I don't know Vala and I've only used sqlite a little, but there are no suggestions so far, so here goes.

Are you sure that the path /Data/Constants.db is correct? What do you get from:
```

ls -l /Data/Constants.db

```
As I recall, the default behaviour of sqlite is to create (if possible) an empty database if the specified file does not exist. What output do you get from running your program?

Using mixed case for table/column names can be problematical with some DBMS if such names are not quoted - I'm not sure what sqlite behaviour is.

If I had your problem, in order to troubleshoot, I would try to simplify it by a) removing the directory specification and b) using lowercase for table and column names.

---

### Post by littledaisyphysics on 2014-04-06
Sorry about not replying sooner, I wasn't expecting a reply actually.

Using
```
ls -l /Data/Constants.db 
```

when I'm in the Constants directory gives me the following output

```
ls: cannot access /Data/Constants.db: No such file or directory
```

If I cd into the Data directory, and just type ls, Constants.db shows up.

I'll try your other suggestions right now.

---

