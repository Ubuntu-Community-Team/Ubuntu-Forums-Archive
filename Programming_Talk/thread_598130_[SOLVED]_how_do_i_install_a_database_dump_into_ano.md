---
title: "[SOLVED] how do i install a database dump into another database?"
date: 2007-10-31
forum: Programming Talk
---

### Post by frietzieey on 2007-10-31
i have a new database called 'jabb' and i want install the dump file 'sample.sql' into it?.. ive tried mysqldump --opt jabb > sample.sql but when i chek jabb, there aren't no tables.. do i still have to make the tables before dumping?

---

### Post by frietzieey on 2007-10-31
by the way im using ruby... and how do i make a ruby application connecting to the 'jabb' database?..

---

### Post by evymetal on 2007-10-31
> **frietzieey said:**
> i have a new database called 'jabb' and i want install the dump file 'sample.sql' into it?.. ive tried mysqldump --opt jabb > sample.sql but when i chek jabb, there aren't no tables.. do i still have to make the tables before dumping?


**mysqldump jabb -u [username] -p > sample.sql **
Should export the table jabb _from mysql to SQL syntax in a file called sample.sql_. (if this isn't what you wanted to do you may have to get a fresh file.) open this file:

**gedit sample.sql **(I'd use vim sample.sql)

And check that the file contains the table.

The command for importing a dump is something like

**mysql jabb -u[username] -p < sample.sql**

If that doesn't work then I think you must not have mysql users set up correctly (check out the mysql manual - it's actually really well documented)

---

### Post by frietzieey on 2007-10-31
> **evymetal said:**
> 
The command for importing a dump is something like

**mysql jabb -u[username] -p < sample.sql**

If that doesn't work then I think you must not have mysql users set up correctly (check out the mysql manual - it's actually really well documented)

thanks.. it did work for me!! next thing that my teacher wants me to do is something like this.. 

On the "jabb" database, there is a table named "authreg" which
 
have fields (username, realm, password)
Write a ruby application that will connect to the mySQL server and
 
query the contents of the table "authreg". Display the result in this
 
format:

|  Username   |  Realm       |  Password  |
|  alvin            |  localhost   |  foobar       |
and so on...
4. Also write a ruby application that will Update/Insert/Delete
 records 
from the "authreg" table.

ive read tutorials bout making a ruby web application but i can't seem to follow it.. i only have little knowledge of simple coding in ruby..

---

### Post by evymetal on 2007-11-04
sorry, never used Ruby, but you'll have to:

create a database connection

Prepare a  command

Execute that command

Get any data back

Close the connection

(plus one or two other steps)

---

