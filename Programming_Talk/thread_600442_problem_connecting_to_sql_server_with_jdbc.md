---
title: "problem connecting to sql server with jdbc"
date: 2007-11-02
forum: Programming Talk
---

### Post by biggie_mac on 2007-11-02
Hi, i'm having a problem connecting to a named instance of a sql server 2000 database. In windows in my jsp file I simply write:

con=DriverManager.getConnection("jdbc:microsoft:sqlserver://servername\\instancename;databaseName=dbname;selectMethod=cursor;","user","pass");

if I run the same jsp from ubuntu i get 
The requested instance is either invalid or not running.

if instead of the instance name I put the port on which the instance runs it works. but I need to use the instance name for various reasons...did anybody had a similar problem or knows why I get this error? why in ubuntu I cant connect using the instance name? 10x

---

