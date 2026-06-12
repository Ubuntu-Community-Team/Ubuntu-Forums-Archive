---
title: "Could not connect to master backend server"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by cjgump720 on 2012-10-31
My wife is a school teacher and just got a bunch of Ubuntu boxes donated for use.  I took this as a chance to finally build a mythbuntu DVR.  This is my first time working with linux, and its been going pretty smooth so far.  I found a post in these forums to fix a sound problem, but now I'm getting an error every time I run the front end:

> Could not connect to the master backend server.  Is it running?  Is the IP address set for it in mythtv-setup correct?I have only one machine running both the front and back ends.  In the backend setup, I've tried using both the localhost as the IP address, and the one assigned by the router.  I've done two installs (as a part of fixing the sound problem), but I'm pretty sure that it worked at first on my current install, and then started giving me this error later.  

When I search for this error, I find plenty of posts, but they're all for people having problems with separate front and backends.  I'm not sure what else to try.  

I'm running Mythbuntu 12.04 on an AMD/ATI board with an A4 processor.  I'm not sure what other info might be useful.

Thanks,

chris

---

### Post by cjgump720 on 2012-11-06
OK, so I've continued looking for solutions.  One possible suggestion was that there was a problem with either my config.xml or my mysql.txt files.

config.xml:  I'm not sure if the DBPort is specified correctly.  It doesn't seem to match up with any of the ports listed in mythtv-setup.


> <Configuration>
  <UPnP>
    <MythFrontend>
      <DefaultBackend>
        <DBHostName>localhost</DBHostName>
        <DBUserName>mythtv</DBUserName>
        <DBPassword>cR99xukC</DBPassword>
        <DBName>mythconverg</DBName>
        <DBPort>3306</DBPort>
      </DefaultBackend>
    </MythFrontend>
    <UDN>
      <MediaRenderer>{9f70e388-5137-49cc-9c06-08eb498800a</MediaRenderer>
    </UDN>
  </UPnP>
</Configuration>

mysql.txt.  I'm at a loss with this one, but I do see that it uses the same DBPort that config.xml does.

> DBHostName=localhost

# By default, Myth tries to ping the DB host to see if it exists.
# If your DB host or network doesn't accept pings, set this to no:
#
#DBHostPing=no

DBPort=3306
DBUserName=mythtv
DBPassword=cR99xukC
DBName=mythconverg
DBType=QMYSQL

# Set the following if you want to use something other than this
# machine's real hostname for identifying settings in the database.
# This is useful if your hostname changes often, as otherwise you
# will need to reconfigure mythtv every time.
# NO TWO HOSTS MAY USE THE SAME VALUE
#
#LocalHostName=my-unique-identifier-goes-here

# If you want your frontend to be able to wake your MySQL server
# using WakeOnLan, have a look at the following settings:
#
#
# The time the frontend waits (in seconds) between reconnect tries.
# This should be the rough time your MySQL server needs for startup
#
#WOLsqlReconnectWaitTime=0
#
#
# This is the number of retries to wake the MySQL server
# until the frontend gives up
#
#WOLsqlConnectRetry=5
#
#
# This is the command executed to wake your MySQL server.
#
#WOLsqlCommand=echo 'WOLsqlServerCommand not set'

One final possibility I found was that the permissions for the MySQL tables might be set up wrong.  But I can't seem to check on that.  When I try to open mysql, I get an error:

> chris@HTPC-TA75M:~/.mythtv$ mysql -u root mysql
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


Can someone help me interpret these things to see if it might be the cause of my problems?

Thanks,

chris

---

### Post by cjgump720 on 2012-11-08
OK, I'm back again after more searching.  I'm somewhat blindly following commands, here's what I got.

I check whether mysql and the backend are running:

> chris@HTPC-TA75M:~$ sudo netstat -ltnp |grep my
[sudo] password for chris: 
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      982/mysqld      

Aha! No mythbackend.  So I try and start it:


> chris@HTPC-TA75M:~$ sudo service mythtv-backend start
mythtv-backend start/running, process 2866
chris@HTPC-TA75M:~$ sudo netstat -ltnp |grep my
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      982/mysqld      


Still not there.  Any ideas on why my backend won't start?  If I'm way off base here, forgive me.

chris

---

### Post by cjgump720 on 2012-11-28
OK, I finally had some more time to play around with it, and decided to do a reinstall of mythbuntu.  Everything seemed to be working ok until I set up the HDHomerun capture card.  I set them up using the MythTV Backend Setup.  MythTV recognized the tuner box and accepted the setup.  Then I got the same Could Not Connect error with the frontend.  I went back into the backend setup and deleted the capture cards, and the error in the frontend went away.  So it seems likely that the tuner box is causing the problem.  From there I'm at a loss.  

My home network assigns IP addresses dynamically.  Could that be the cause?  Should I assign static IPs to the tuner box and the MythTV box?

Thanks

---

### Post by bab1 on 2012-11-29
> **cjgump720 said:**
> ...
My home network assigns IP addresses dynamically.  Could that be the cause?  Should I assign static IPs to the tuner box and the MythTV box?

Thanks

If the two hosts (frontend and backend) need to talk to each other then it might be wise to at least try assigning non-changing IP addresses.  Do you configure the IP address or hostname anywhere in the configuration files?  How is the data processed from the backend to the frontend or visa versa?

At this point this host is only talking to itself```
tcp 0 0 **[COLOR="Red"]127.0.0.1[/COLOR]**:3306 0.0.0.0:* LISTEN 982/mysqld
```...and there is no MythTV server running here.

I have to admit I have never set up MythTV.  I'm just looking at the problem from a networking standpoint.

---

### Post by cjgump720 on 2012-12-03
I'm wondering if the problem is my network connection.  In the interest of time and convenience, I used a wireless bridge plugged into my ethernet port on the mythtv box.  So maybe that's causing a communication problem when the it tries to communicate with the hdhomerun through the router.  

I'm bringing home a spare wireless adapter from work; we'll see if that fixes the problem.

chris

---

### Post by cjgump720 on 2012-12-21
I can't guarantee that I know what fixed it, but I was able to stop the error with help over in this thread:

[http://ubuntuforums.org/showthread.php?t=2095793](http://ubuntuforums.org/showthread.php?t=2095793)

---

