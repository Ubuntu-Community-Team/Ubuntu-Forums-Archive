---
title: "DBVisualizer Connection problem"
date: 2005-02-27
forum: Programming Talk
---

### Post by bingo11 on 2005-02-27
Hi all,

I have installed DBVisualizer few days ago and have had some problems
connecting to a remote database. My jre is the following version :
java version "1.5.0_01"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_01-b08)
Java HotSpot(TM) Client VM (build 1.5.0_01-b08, mixed mode, sharing)

My SQL connector is 3.0.9. This is the connector i use with Fedora 3
from work to connect to that same database with DBvisualizer.

The mysql version i am trying to connect to is : mysql  Ver 11.18
Distrib 3.23.58, for redhat-linux-gnu (i386)

When trying to connect the "Connecting. wait..." is displayed for a
while in the connection message area,  then a debug window pops up
with the following message :

java.sql.SQLException: Unable to connect to any hosts due to
exception: java.net.ConnectException: Connection timed out
       at com.mysql.jdbc.Connection.createNewIO(Connection.java:1797)
       at com.mysql.jdbc.Connection.<init>(Connection.java:562)
       at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:361)
       at java.sql.DriverManager.getConnection(DriverManager.java:512)
       at java.sql.DriverManager.getConnection(DriverManager.java:140)
       at com.onseven.dbvis.wrapper.DriverManagerImpl.getConnection(DriverManagerImpl.java:40)
       at com.onseven.dbvis.sql.Database.doConnect(Unknown Source)
       at com.onseven.dbvis.sql.Database.access$000(Unknown Source)
       at com.onseven.dbvis.sql.Database$ConnectionCommand.execute(Unknown Source)
       at se.pureit.util.ThreadCommand.runExecute(ThreadCommand.java:163)
       at se.pureit.util.ThreadCommand.run(ThreadCommand.java:143)
       at java.lang.Thread.run(Thread.java:534)
java.sql.SQLException: Unable to connect to any hosts due to
exception: java.net.ConnectException: Connection timed out
       at com.mysql.jdbc.Connection.createNewIO(Connection.java:1797)
       at com.mysql.jdbc.Connection.<init>(Connection.java:562)
       at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:361)
       at java.sql.DriverManager.getConnection(DriverManager.java:512)
       at java.sql.DriverManager.getConnection(DriverManager.java:140)
       at com.onseven.dbvis.wrapper.DriverManagerImpl.getConnection(DriverManagerImpl.java:40)
       at com.onseven.dbvis.sql.Database.doConnect(Unknown Source)
       at com.onseven.dbvis.sql.Database.access$000(Unknown Source)
       at com.onseven.dbvis.sql.Database$ConnectionCommand.execute(Unknown Source)
       at se.pureit.util.ThreadCommand.runExecute(ThreadCommand.java:163)
       at se.pureit.util.ThreadCommand.run(ThreadCommand.java:143)
       at java.lang.Thread.run(Thread.java:534)

I would really appreciate if you could give me any pointers about how
to resolve this problem.

Thank you for your cooperation,

Madi

---

### Post by mrhacim on 2007-02-19
I was having the same problem here. I found that I had unknowingly upgraded to java 6. I was trying to connect to MS Sql Server and DbVis was using the java 6 version of the driver and it seems that this driver was causing the exception. So I loaded in my old driver and it worked just like before.

Hope that helps.

---

