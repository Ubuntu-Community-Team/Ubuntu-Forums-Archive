---
title: "[SOLVED] Java/Firefox problem (Managerzone 3D)"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Cristi73 on 2008-09-18
I'm quite new to Linux in general and especially to Ubuntu, but I managed to get all devices working, including the AR5007G wireless card, this forum.
Now I have a new problem and I can't seem to find an answer.

I installed sun java via package manager (fonts and plugin as well) and it works. HattrickOrganizer, a platform independet aplication writen in java works fine and on the test page from java the plugin seems to be working.
The problem is with a java match viewer from the browsergame Managerzone, the applet won't start. I enabled the console and here is what it says:

> Java Plug-in 1.6.0_06
Using JRE version 1.6.0_06 Java HotSpot(TM) Client VM
User home directory = /home/cristian


----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

*** STARTING POWERLOADER APPLET ***
Base domain of download host: managerzone.com
Applet: window display mode 
Running on Linux
*** STARTING APPLICATION ***
*** CREATING WORKER THREAD ***
*** RUNNING WORKER THREAD ***
Application: rendering to new window
*** INITIALIZING NATIVE SUBSYSTEM ***
Initializing system: default
WebDriver v0.8.9-2
Home: /tmp/cristian/mzlive/
Packages to download: sys.zip,std.zip,toyota.zip,df.zip,data.zip,..//data/soccer/7/8/stats267497287.xml.gz,..//data/soccer/7/8/data267497287.gz,..//data/soccer/7/8/livescores267497287.2680257.xml.gz
Package: sys.zip
Package: std.zip
Package: toyota.zip
Package: df.zip
Package: data.zip
Package: ..//data/soccer/7/8/stats267497287.xml.gz
Package: ..//data/soccer/7/8/data267497287.gz
Package: ..//data/soccer/7/8/livescores267497287.2680257.xml.gz
0
Inside cache lib
File cache: libneowebdriver.so libcounter 0
libneowebdriver.so: requesting: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
libneowebdriver.so: protocol: http
libneowebdriver.so: got HTTP connection
libneowebdriver.so: opening URL connection
libneowebdriver.so: got connection
libneowebdriver.so: got response code: 404
libneowebdriver.so: got content-length header: 345
libneowebdriver.so: got last-modified header: null
libneowebdriver.so: WARNING: connection failed: java.io.FileNotFoundException: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
File cache: libneowebdriver.so libcounter 1
libneowebdriver.so: requesting: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
libneowebdriver.so: protocol: http
libneowebdriver.so: got HTTP connection
libneowebdriver.so: opening URL connection
libneowebdriver.so: got connection
libneowebdriver.so: got response code: 404
libneowebdriver.so: got content-length header: 345
libneowebdriver.so: got last-modified header: null
libneowebdriver.so: WARNING: connection failed: java.io.FileNotFoundException: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
File cache: libneowebdriver.so libcounter 2
libneowebdriver.so: requesting: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
libneowebdriver.so: protocol: http
libneowebdriver.so: got HTTP connection
libneowebdriver.so: opening URL connection
libneowebdriver.so: got connection
libneowebdriver.so: got response code: 404
libneowebdriver.so: got content-length header: 345
libneowebdriver.so: got last-modified header: null
libneowebdriver.so: WARNING: connection failed: java.io.FileNotFoundException: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
File cache: libneowebdriver.so libcounter 3
libneowebdriver.so: requesting: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
libneowebdriver.so: protocol: http
libneowebdriver.so: got HTTP connection
libneowebdriver.so: opening URL connection
libneowebdriver.so: got connection
libneowebdriver.so: got response code: 404
libneowebdriver.so: got content-length header: 345
libneowebdriver.so: got last-modified header: null
libneowebdriver.so: WARNING: connection failed: java.io.FileNotFoundException: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
File cache: libneowebdriver.so libcounter 4
libneowebdriver.so: requesting: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
libneowebdriver.so: protocol: http
libneowebdriver.so: got HTTP connection
libneowebdriver.so: opening URL connection
libneowebdriver.so: got connection
libneowebdriver.so: got response code: 404
libneowebdriver.so: got content-length header: 345
libneowebdriver.so: got last-modified header: null
libneowebdriver.so: WARNING: connection failed: java.io.FileNotFoundException: [http://download09.managerzone.com/soccer-3d/libneowebdriver.so](http://download09.managerzone.com/soccer-3d/libneowebdriver.so)
Unable to read library libneowebdriver.so
Error initializing webdriver
*** TERMINATING APPLICATION ***
nullify worker thread
garbage collect
*** TERMINATED ***


---

### Post by MegaJim on 2008-09-18
This isn't a linux problem, it is a problem with either the website (packages not available) or the applet; contact the maker of the applet.

---

### Post by Cristi73 on 2008-09-18
> **MegaJim said:**
> This isn't a linux problem, it is a problem with either the website (packages not available) or the applet; contact the maker of the applet.

I guess it is a linux problem since it work fine under Windows with FF or IE...

---

### Post by MegaJim on 2008-09-18
No, the applet tries to detect the operating system in use and load appropriate files; the files it tries to load however do not exist on the server.

---

### Post by Cristi73 on 2008-09-19
You're right, sorry. They don't have a linux version. Only Windows and Mac OSX :(

---

