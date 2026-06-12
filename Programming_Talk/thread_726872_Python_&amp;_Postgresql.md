---
title: "Python &amp; Postgresql"
date: 2008-03-17
forum: Programming Talk
---

### Post by rax_m on 2008-03-17
Hi, 

I've recently started programming in Python. What I need to do is write a Python script that uses the PostgreSQL bulk copy functionality. This function allows the bulk insert of data from a flat file into a table.

I've looked at a number of Python modules but can't seem to find much documentation or tutorials:
PyGreSQL
pgdb
psycopg2

Does anyone know of any good ways of doing this? 

Thanks
Rax

---

### Post by rax_m on 2008-03-17
Well, if anyone's interested, I finally found this kind of helpful site:

[http://wiki.python.org/moin/DatabaseInterfaces](http://wiki.python.org/moin/DatabaseInterfaces)

Unfortunately, none of these interfaces seem to be documented or give good examples so it makes starting kind of difficult.

---

### Post by themusicwave on 2008-03-17
I'm not sure if it will work, but some of the Postgres functionality is actually provided by little programs in the install directory.

I know that the backup functionality is this way.  I was able to create a program to run and schedule postgres backups by hooking into this program and sending the right arguments.  Perhaps you could do the same?

---

### Post by ruy_lopez on 2008-03-17
To qualify myself, I know next to nothing about Postgresql.

Why are you trying to do this with a python script? From what I can see, pygresql is mainly used for output. You connect to the db, run a query, and then process the output.

For bulk copying I would use the command line:
```

psql -d dbname < bulk_dumpfile

```

Try pygresql with the COPY command. I haven't used it with COPY before, but you can try it.
```

import pg

# use None for the options you don't need
# or -1 for 'port' if you don't need to set the port.
conn = pg.connect('dbname', 'host', port, 'opt', 'user', 'password') 
res = conn.query("<COPY code here>")


```

See [this]("http://www.pygresql.org/pg.html#query-executes-a-sql-command-string") for details of using query().

---

### Post by rax_m on 2008-03-17
Hi guys

Thanks for the replies. 
Well, what I'm actually trying to do is create an automated script for import of data. 
A user gets an XLS sheet from someone containing a few thousand rows of data. I'm trying to script the conversion of the file into CSV and then auto-upload into the database (possibly a temp table to check for errors before appending to the original table). 

Ruy_lopez - I've just been looking at alternatives of running the psql command from a script with a sql file. This seems to work so I'll probably do that instead of the python script. Something like 
```

psql -h localhost -d Test -v input="'/home/rmistry/test.csv'" -f import.sql

```
So the sql script handles the COPY command. 

themusicwave - thanks for the hint.. I'll check it out. 

Unfortunately the issue I'm having now is that pyExcelerator does not convert Excel dates correctly (yep.. I know it's Excels fault ;) ) So trying to find alternatives. 

Cheers
Rax

---

