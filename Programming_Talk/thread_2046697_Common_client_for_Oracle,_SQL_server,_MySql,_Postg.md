---
title: "Common client for Oracle, SQL server, MySql, Postgresql, SQLite"
date: 2012-08-23
forum: Programming Talk
---

### Post by vikkyhacks on 2012-08-23
I found a software "navicat" which can act as a client for mysql, oracle, sql server, mysql and sqlite ... I downloaded the trial copy and found that it uses wine to run on ubuntu ... I din like it but the idea was good that the software can support all db servers ... Are there any other software which can do the same ... ie can act as a client for Oracle, SQL server, MySql, Postgresql, SQLite .... ????

---

### Post by ofnuts on 2012-08-24
> **vikkyhacks said:**
> I found a software "navicat" which can act as a client for mysql, oracle, sql server, mysql and sqlite ... I downloaded the trial copy and found that it uses wine to run on ubuntu ... I din like it but the idea was good that the software can support all db servers ... Are there any other software which can do the same ... ie can act as a client for Oracle, SQL server, MySql, Postgresql, SQLite .... ????
For all my database needs (looking at table contents, writing queries). I use[ Squirrel]("http://squirrel-sql.sourceforge.net/"). It supports all DBMs for which there is a JDBC driver, so that pretty much includes everybody.

---

### Post by vikkyhacks on 2012-08-25
Thanks for the reply ....
I loves that tool and am using it ... the only thing that irritates me is the small ugly font that it has ... how do i change the font size of the queries that i type ????

---

### Post by berenErchamion on 2012-08-25
I agree - squirrel is the way to go.

---

### Post by ofnuts on 2012-08-25
> **vikkyhacks said:**
> Thanks for the reply ....
I loves that tool and am using it ... the only thing that irritates me is the small ugly font that it has ... how do i change the font size of the queries that i type ????
Global preferences (icon in top tool bar, right next to the "Connect to" field), "Fonts" tab.

---

### Post by vikkyhacks on 2012-08-25
> **ofnuts said:**
> Global preferences (icon in top tool bar, right next to the "Connect to" field), "Fonts" tab.

I tried this one ... the problem is it can change any font except the query window and I need to change only the query window and keep all the other fonts as it is ....

---

### Post by ofnuts on 2012-08-25
> **vikkyhacks said:**
> I tried this one ... the problem is it can change any font except the query window and I need to change only the query window and keep all the other fonts as it is ....
This font seems to be set "per session". See:
[http://squirrel-sql.sourceforge.net/user-manual/quick_start.html](http://squirrel-sql.sourceforge.net/user-manual/quick_start.html) in section "New Session and Session Properties"

Edit: just checked... the doc above is obsolete, but the functionality is there:

"<menubar>/Session/Session properties" then, "SQL" tab, and scroll to bottom to the "SQL entry area" section.

You can also set it as a default for new sessions:  "<menubar>/File/New session properties", then same.

---

### Post by jiminlexky on 2012-08-26
First time for me to use the forums!  I have installed MySQL server and it is working well.  I am now trying to write C code to put data into the DB.  The .H files are not in the correct place and I have not been able to find any references for getting them installed.  Using 12.04 distribution.  Any help would be very much appreciated!

---

### Post by ofnuts on 2012-08-27
> **jiminlexky said:**
> First time for me to use the forums!  I have installed MySQL server and it is working well.  I am now trying to write C code to put data into the DB.  The .H files are not in the correct place and I have not been able to find any references for getting them installed.  Using 12.04 distribution.  Any help would be very much appreciated!
This is a very different question and you should start a new thread for this...

---

