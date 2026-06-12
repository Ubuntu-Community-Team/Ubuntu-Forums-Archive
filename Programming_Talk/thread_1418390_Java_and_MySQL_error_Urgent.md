---
title: "Java and MySQL error *Urgent"
date: 2010-02-28
forum: Programming Talk
---

### Post by Sugz on 2010-02-28
Hello all, 
a recently discovered bug in a program has forced me to slightly rethink my Database structure.

```
    try
            {
            statement.execute("CREATE TABLE `" + databaseName +
             "`.`X`" +
             " (`Fone` INT UNSIGNED NOT NULL REFERENCES Y(Y_id), " +
             "`Ftwo` INT UNSIGNED NOT NULL REFERENCES Z(Z_id), "+
             "`Fthree` INT UNSIGNED NOT NULL, "+
             "PRIMARY KEY (Fone, Ftwo, Fthree))");
            }
            catch(SQLException e)
            {
                //Ignore error code 1050, table already exists
                if(e.getErrorCode() != 1050)
                {
                    Utils.logError("D0DatabaseCon",
                                   "createDatabaseStructure",
                                   "Exception: " + e.getMessage());
                }
            }
```
*Fields and table names do not reflect actual implementation*


Above is the try statement I use to create the MySQL table, however this is exiting and catching an exeption, which claims that there is an error in my syntax near "Fthree))"

I have been working for hours to try and fix this, and I cannot find a solution. 
I have used composite primary keys elsewhere in my program with success this one just seems to be a problem

---

### Post by mike_g on 2010-03-01
I'm not sure, but you are using a database engine that supports references right? IIRC the default, MyISAM, does not, you need InnoDB or something.

Also, you could start you statement with:
```
CREATE TABLE IF NOT EXISTS 
```
Then you would not have to deal with MySQL errors if the table exists.

---

