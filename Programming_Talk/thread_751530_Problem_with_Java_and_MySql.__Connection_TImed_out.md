---
title: "Problem with Java and MySql.  Connection TImed out"
date: 2008-04-10
forum: Programming Talk
---

### Post by jhall834 on 2008-04-10
Hey there!

We recently set up a new staging machine with Ubuntu at my work.  I have been trying to deploy a Java application on this machine and have been getting Connection Timed Out messages when Hibernate tries to connect to the Database.  I am pretty sure there are no Spring/Hibernate issues because the same config files are being used in production as well as on developer machines and connections work fine to MySql there.  We are using Red Hat in Production and Windows/Mac for developers so we are guessing it is some issue with our Ubuntu configuration and/or MySql installation on this machine.

When I connect to MySql with the command line 'mysql...' I am able to connect fine.  It is only when I try and connect via java/jdbc that I am having problems with the timeout.

To further rule out something non MySql/Ubuntu I followed this little guide [https://help.ubuntu.com/community/JDBCAndMySQL](https://help.ubuntu.com/community/JDBCAndMySQL)

I created a new user for this test that I can log in via the mysql command.  When I compile and run the program I get the same Connection Timed out error I got in the production app.

java.net.SocketException
MESSAGE: java.net.ConnectException: Connection timed out

STACKTRACE:

java.net.SocketException: java.net.ConnectException: Connection timed out
        at com.mysql.jdbc.StandardSocketFactory.connect(StandardSocketFactory.java:156)
        at com.mysql.jdbc.MysqlIO.<init>(MysqlIO.java:277)
        at com.mysql.jdbc.Connection.createNewIO(Connection.java:2668)
        at com.mysql.jdbc.Connection.<init>(Connection.java:1531)
        at com.mysql.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:266)
        at java.sql.DriverManager.getConnection(DriverManager.java:525)
        at java.sql.DriverManager.getConnection(DriverManager.java:140)
        at DBDemo.main(DBDemo.java:30)


Anyone have any insight for me on this one?  Let me know of any system/config files I might need to look into.  None of us here know much about Ubuntu so we are a bit stuck right now on this.

Thanks

---

### Post by kevykev on 2008-04-10
I'm not sure if it's related, but I had some problems before with ubuntu performing reverse dns lookups on ip addresses. This caused connection timeouts in places with dns servers with reverse dns disabled. 

The problem happened for me back in feisty. I fixed it then by changing the /etc/nsswitch.conf file. I'm not sure if they fixed it since. but it might be what's causing your problems. Check out [this launchpad bug]("https://bugs.launchpad.net/debian/+source/nss-mdns/+bug/94940") for more info.

---

### Post by jhall834 on 2008-04-10
> **kevykev said:**
> I'm not sure if it's related, but I had some problems before with ubuntu performing reverse dns lookups on ip addresses. This caused connection timeouts in places with dns servers with reverse dns disabled. 

The problem happened for me back in feisty. I fixed it then by changing the /etc/nsswitch.conf file. I'm not sure if they fixed it since. but it might be what's causing your problems. Check out [this launchpad bug]("https://bugs.launchpad.net/debian/+source/nss-mdns/+bug/94940") for more info.

Thanks I'll give it a shot (or maybe already have).  When I edit that /etc/nsswitch.conf file' is there anything that needs to be restarted to pick up the changes?  If not and it is dynamic I tried a few of the suggestions in the thread and am still getting the same problem.

---

### Post by jhall834 on 2008-04-11
Ok this was pretty goofy.  

After narrowing this down to MySql/Ubuntu we went through this

[http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer](http://forge.mysql.com/wiki/Error2003-CantConnectToMySQLServer)

Everything pretty much checked out.  Client/Server agreed on the Port and the Socket.  We could login to Mysql from remote clients via TCP and locally via Unix Socket but not TCP.

We could also 'telnet 'localhost 3306' remotely but not locally.  Pretty odd!

Of course it ends up being something simple.  The person who installed Ubuntu was having problems getting networking up and probably messed  around a bit with /etc/network/interfaces in the process.  When we looked at this file it was set up for remote but not local ethernet.  We updated this for local and everything is now working fine.

---

