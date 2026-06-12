---
title: "Installing OpenNMS on Hardy Heron"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Jordan247 on 2008-08-08
Has anyone had luck with installing a stable/unable OpenNMS release on Hardy Heron or other Ubuntu releases?  I have followed the ubuntu install guide on OpenNMS and had no luck.  

Could somebody lead me in the right direction as per install documentation that will work?

P.S - Will postgresql 8.2/8.3 work now?


Thanks in advance,

Jordan

---

### Post by timcredible on 2008-08-08
a person at work installed it as a test on 7.04, worked no problem, as i recall, they got all dependencies from synaptic.

---

### Post by Jordan247 on 2008-08-08
Could you please explain more of this "got the dependencies from synaptic"? - Would that require me installing the desktop version of ubuntu instead of server?  It appears there is no GUI on the server one - I am an uber noob to ubuntu - Cheers

Jordan

---

### Post by bgsneeze on 2008-08-13
I would also like to know if there is a way to get OpenNMS working on 8.04. I cant get all of the dependencies working.

---

### Post by wirelessmonkey on 2008-08-13
I just installed it to see if I could get it working. Yep, I can ;)

These are the steps I took...

First, edit /etc/apt/sources.list and add

 ```
deb http://debian.opennms.org unstable main
 deb-src http://debian.opennms.org unstable main

```

then 
```
 wget -O - http://debian.opennms.org/OPENNMS-GPG-KEY | sudo apt-key add -
```

then
 ```

export SKIP_IPLIKE_INSTALL=1
sudo apt-get update
sudo apt-get install sun-java5-sdk opennms
export OPENNMS_HOME=/usr/share/opennms
/etc/init.d/postgresql-8.2 start

```

Now edit /etc/postgresql/8.2/main/pg_hba.conf so the last few lines look like this: 

```
local   all         postgres                          trust

# TYPE  DATABASE    USER        CIDR-ADDRESS          METHOD                    

# "local" is for Unix domain socket connections only                            
local   all         all                               trust
# IPv4 local connections:                                                       
host    all         all         127.0.0.1/32          trust
# IPv6 local connections:                                                       
host    all         all         ::1/128               trust


```

Now restart postgres and continue:

```
sudo /etc/init.d/postgresql-8.2 restart
sudo $OPENNMS_HOME/bin/runjava -S /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/bin/java
```

Now edit /etc/default/opennms, it should be blank to start...

```
JAVA_HOME=/usr
```

and Last

```
 $OPENNMS_HOME/bin/install -dis
```


If all has gone well, you should be able to connect to opennms at [http://127.0.0.1:8980/opennms/](http://127.0.0.1:8980/opennms/)

---

### Post by Cato2 on 2008-10-03
wirelessmonkey, thanks for the mini HOWTO!  I got OpenNMS installed pretty quickly on Ubuntu 7.10, and it was a lot easier than the Debian HOWTO on the OpenNMS site.

One significant typo - the apt-get line should say -jdk not -sdk:
```
sudo apt-get install sun-java5-jdk opennms
```

Also, the web GUI for OpenNMS (via Jetty) actually listens on all interfaces by default, not just 127.0.0.1.  Convenient for small networks but worth knowing if security is an issue - change the password ASAP or edit the /etc/opennms/opennms.properties file, uncommenting the last line, to only listen on localhost:
```
# By default, Jetty will listen on all interfaces. You can set a specific
# bind address here. If you set this to a value other than 127.0.0.1,
# you will need to update the rtc-client and map-client URLs above.
#org.opennms.netmgt.jetty.host = 127.0.0.1
```

It's also a good idea to edit /etc/postgresql/8.2/main/postgresql.conf for the same reason, and restart PostgreSQL, unless you want OpenNMS's GUI to be remotely accessible.

To discover devices, you can edit /etc/opennms/discovery-configuration.xml to specify an IP address range to discover, then restart OpenNMS.

Once the GUI is up, the default userid and password is 'admin'.  Overall it's pretty nice, a very powerful system but not hard to get it going in a basic mode.  Enabling SNMP on the nodes you are monitoring really helps, as you can get a lot of handy performance and availability data as Resource Graphs without much effort.

---

### Post by Cato2 on 2008-10-04
Moderators - can someone move this thread to 'Server Platforms' forum?  OpenNMS is an enterprise-level network management tool so I don't think it belongs in 'Absolute Beginner Talk' :)

---

