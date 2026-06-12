---
title: "SQLException (errno: 150) in Ubuntu but not in Windows Vista"
date: 2011-06-20
forum: Programming Talk
---

### Post by skytreader on 2011-06-20
Hi all. I'm making a JDBC-driven application and it runs perfectly fine in Windows but not in Ubuntu. The Ubuntu error message goes:

```
java.sql.SQLException: Can't create table 'dbname.timelogs' (errno: 150)
	at com.mysql.jdbc.SQLError.createSQLException(SQLError.java:1073)
	at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3597)
	at com.mysql.jdbc.MysqlIO.checkErrorPacket(MysqlIO.java:3529)
	at com.mysql.jdbc.MysqlIO.sendCommand(MysqlIO.java:1990)
	at com.mysql.jdbc.MysqlIO.sqlQueryDirect(MysqlIO.java:2151)
	at com.mysql.jdbc.ConnectionImpl.execSQL(ConnectionImpl.java:2619)
	at com.mysql.jdbc.StatementImpl.executeUpdate(StatementImpl.java:1698)
	at com.mysql.jdbc.StatementImpl.executeUpdate(StatementImpl.java:1617)
	at net.skytreader.kode.utils.DatabaseDriver.createTablesStructures(DatabaseDriver.java:119)
	at net.skytreader.kode.utils.DatabaseDriver.<init>(DatabaseDriver.java:65)
	at net.skytreader.kode.tasktimer.TaskTimerRunnable.createDatabase(TaskTimerRunnable.java:157)
	at net.skytreader.kode.tasktimer.TaskTimerRunnable.run(TaskTimerRunnable.java:92)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
	at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:647)
	at java.awt.EventQueue.access$000(EventQueue.java:96)
	at java.awt.EventQueue$1.run(EventQueue.java:608)
	at java.awt.EventQueue$1.run(EventQueue.java:606)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:617)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```

(Another NullPointerException followed but that is from my code, which expects something from a database).

I read [here]("http://confluence.atlassian.com/display/CONFKB/Database+Errors+when+Using+MySQL+and+MyISAM+Tables") that this is because MyISAM doesn't support foreign key constraints and yes I am using foreign key constraints. However, it works perfectly fine in Vista. So....?

Set-up wise, the only difference I can think of is the XAMPP server I am running. I'm running 1.7.3 in Vista while Ubuntu runs 1.7.4 . Unless I am mistaken, that's not supposed to matter, right?

---

### Post by skytreader on 2011-06-20
*bump*

---

### Post by nklatt on 2011-06-20
What query is causing this error?

---

### Post by skytreader on 2011-06-21
> **nklatt said:**
> What query is causing this error?

Java statement:
```

stmt.executeUpdate(createTableStatement);

```

Where createTableStatement is
```
CREATE TABLE IF NOT EXISTS timelogs(
timestarted DATETIME NOT NULL,
timeended DATETIME NOT NULL,
taskid INTEGER NOT NULL,
PRIMARY KEY (timestarted),
FOREIGN KEY (taskid) REFERENCES tasks)
```

Just for reference, tasks table was created through
```
CREATE TABLE IF NOT EXISTS tasks(
taskid INTEGER NOT NULL AUTO_INCREMENT,
taskperformed VARCHAR(140) UNIQUE NOT NULL,
PRIMARY KEY (taskid))
```

---

### Post by nklatt on 2011-06-21
Just to get the obvious out of the way, is it possible the DB on Vista is *not* MyISAM but InnoDB, perhaps? The default changed with MySQL 5.5.

---

### Post by skytreader on 2011-06-21
> **nklatt said:**
> Just to get the obvious out of the way, is it possible the DB on Vista is *not* MyISAM but InnoDB, perhaps? The default changed with MySQL 5.5.

MySQL Server and Client is version 5.1.41 (taken from phpMyAdmin - Vista).

When I click on the DB created at Vista, the tables have, indeed, type MyISAM.

Later (I'm in GMT+8 ), I'll try to install XAMPP 1.7.4 in Vista and note the behavior. I'll also check what the default table type is created in Ubuntu (the tasks table still gets created).

Thank you very much for bothering. (--,)

---

### Post by nklatt on 2011-06-21
I suppose the next question might be, do the foreign keys work on Vista? :) I guess you did say it works perfectly fine...

Wish I could just tell you what's going on but I really don't know. Keep the conversation going, though, and hopefully someone more knowledgeable will be able to point you right to it.

Say, according to this:
[http://dev.mysql.com/doc/workbench/en/wb-foreign-key-relationships.html](http://dev.mysql.com/doc/workbench/en/wb-foreign-key-relationships.html)

[INDENT]Foreign key constraints are supported for the InnoDB storage engine only. For other storage engines, the foreign key syntax is correctly parsed but not implemented.[/INDENT]

Maybe the foreign key possibility is a red herring?

Have you tried executing the create query by hand? That often generates more helpful messages.

---

### Post by skytreader on 2011-06-22
Ok. This is the first time I actually tried to subject MySQL foreign keys to a sanity test. For all those other times in the past where I used foreign keys, I declared them just to be meticulous about it. And I always did web dev in Windows.

Anyway, same two tables in Vista, in tasks I have only one record

```

+----------------+
|taskid|  task   |
+----------------+
|     1| Testing |
+----------------+

```

Then I tried running the query

```

INSERT INTO  `tasktimer_test`.`timelogs` (
`timestarted` ,
`timeended` ,
`taskid`
)
VALUES (
'2011-06-22 14:39:55', NOW( ) ,  '45'
);

```

and it ran without a hitch. That shouldn't happen right?

> I suppose the next question might be, do the foreign keys work on Vista?  I guess you did say it works perfectly fine...

My bad. When I said it works fine in Vista, what I mean is it compiles and runs without problems, writes to the tables as expected, etc. I haven't tried if the foreign key constraint holds indeed.

Issue closed unless there are additions? (^^,)

---

### Post by skytreader on 2011-06-22
Ok...this is weird.

I was in Vista a little while ago and then I recompiled my class such that it explicitly specifies an InnoDB storage engine. And, guess what? Vista threw the very error I'm asking about here.

Surprised, I switched to Ubuntu. I looked at Ubuntu's phpMyAdmin and found out that MySQL server is version 5.5.8 while client is 5.0.7. The default storage engine used by tasks (the table that got created) is, surprisingly, InnoDB. So, it seems that InnoDB is the one causing the problems all the while (despite all docs saying that InnoDB **should** support foreign key constraints). I got it to work in Ubuntu by running the queries:

```
CREATE TABLE IF NOT EXISTS tasks(
taskid INTEGER NOT NULL AUTO_INCREMENT,
taskperformed VARCHAR(140) UNIQUE NOT NULL,
PRIMARY KEY (taskid)) ENGINE=MYISAM

CREATE TABLE IF NOT EXISTS timelogs(
timestarted DATETIME NOT NULL,
timeended DATETIME NOT NULL,
taskid INTEGER NOT NULL,
PRIMARY KEY (timestarted),
FOREIGN KEY (taskid) REFERENCES tasks) ENGINE=MYISAM

```

Notice that I explicitly specified MyISAM this time around. I guess I'll be sticking with MyISAM for now. While the foreign key constraint doesn't exactly hold for MyISAM, that's where I get my code to run.

(I'll mark this thread [SOLVED] when I verify that it works in Vista. I'm on a dual-boot set-up so should take sometime.)

---

### Post by nklatt on 2011-06-22
Glad to hear things are falling into place. :)

---

