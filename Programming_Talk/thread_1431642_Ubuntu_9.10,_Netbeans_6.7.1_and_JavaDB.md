---
title: "Ubuntu 9.10, Netbeans 6.7.1 and JavaDB"
date: 2010-03-16
forum: Programming Talk
---

### Post by jlanawalt on 2010-03-16
I've been spinning my wheels trying to get this "simple" Netbeans/JavaDB setup for the "Java Desktop Application" project in the ["Building a Java Desktop Database Application" tutorial]("http://netbeans.org/kb/docs/java/gui-db.html").

To start, I didn't have anything in the Services tab except this Hudson Builders tree that wouldn't expand. This "Databases" node everyone was talking about was elusive. The third time I looked at *Database, Base IDE* in Plugins I decided to install it despite the description. ("Required to manage Databases in the Services tab" would have been an early clue-bat.)

Now I had a Databases node, but no Java DB node under it as shown in the picture lower down on the tutorial.

[IMG]http://netbeans.org/images_www/articles/60/java/gui-db/services-db-node.jpg[/IMG]

More searching made me think it was due to JavaDB not really being installed with the Sun Java6 JDK despite conflicting reports. Sure enough, there is sun-java6-javadb so I installed that. Now I had a derby.jar and derbyclient.jar so I was able to add them as the embedded and network drivers in Services > Databases > Drivers, but still no Java DB thing to click on to configure it's install location or manage connections.

Next I tried making Netbeans point at java-6-sun instead of java-6-openjdk with every incantation I could find starting with update-java-alternatives, editing /etc/netbeans.conf and even temporarily adding /etc/jvm with an entry pointing at java-6-sun. No dice.

So, I tried it on Windows Vista and Netbeans 6.8. I don't think the slightly later version is the key though as the 6.1 release notes say ["Java DB Database Server moved to Services window."]("http://netbeans.org/community/releases/61/relnotes.html") Right off the bat I saw the Databases node and the Java DB entry under it despite not having installed "Sun JavaDB" yet. The *Database, Base IDE* Plugin was installed. At this point I should have more setup in Ubuntu than windows but the Java DB entry eludes me. I checked out it's properties on the Windows install and the Java DB Installation and Database Location fields were not set. I installed "Sun JavaDB" and launched Netbeans again. Now those properties are configured and I can start the service, create databases and connect to them.

I came across a post that said to install sun-javadb-core (a suggests on sun-javadb-common that was auto-installed but this wasn't pulled in for some reason. Possibly a mistake on my part. Lots of packages. Confusing to know if I need only the "6" one or not from just package names and brief descriptions.) The post even suggested modifying PATH to include the /usr/share/javadb/bin directory and to export DERBY_HOME. I launched netbeans from the shell where I did that and still no luck.

There must be some little thing missing. I expect that "Java DB" should exist before I even installed sun-java6-javadb or other javadb packages. Perhaps switching to point at java-6-sun is required but it didn't seem to have any effect. It would be nice if installing the javadb packages set some known configuration property that netbeans reads to know where the db install location is as it seemed to do on Windows.

Any help getting this going, especially pointers to threads that somehow have escaped my hours of googling.

---

### Post by kahumba on 2010-03-16
Try getting and installing the official version of NetBeans from netbeans.org. There's enough people complaining and often it's true that it's the confusing way NetBeans is packaged that causes the troubles and installing the official version solves that disconnection/deflection.
another one, also using netbeans from repos:
[http://ubuntuforums.org/showthread.php?t=1431355](http://ubuntuforums.org/showthread.php?t=1431355)

---

### Post by jlanawalt on 2010-05-11
I had downloaded the current official version, 6.8, at your suggestion. The Database and Java DB nodes were in the services tab. 

I tried other plug-ins but wasn't able to figure out what makes the Java DB node appear. I've upgraded to Ubuntu 10.4 and it's NetBeans 6.8 but still no Java DB node. I'm still seeking it, just not as actively since I have a work-around.

Thanks,
-- 
Jacob

---

