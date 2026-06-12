---
title: "Tip for Installing LimeWire"
date: 2006-12-06
forum: Outdated Tutorials &amp; Tips
---

### Post by compengi on 2006-12-06
1. You need to check your java version first and make sure it's installed:

~$ java -version

It should look like this:

java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

If Sun Java JRE is not installed you should install it in order to run LimeWire:

~$ sudo apt-get install sun-java5-jre sun-java5-plugin

2. Now download Limewire .rpm package, in order to install it you need to do some steps:

~$ sudo alien -d LimeWireLinux.rpm

This will convert .rpm package into .deb

3. After the process finishes, you need to install the new .dep package:

~$ sudo dpkg -i limewire.deb

4. Now the final step is to do a little trick to make limewire work:

~$ gksudo gedit /usr/bin/limewire

and change it to

#!/bin/bash
cd /usr/lib/LimeWire
bash runLime.sh

Now LimeWire is installed and read to use. Enjoy! :D

---

### Post by pavel_kbc on 2006-12-07
root@r00t-suck-on-that:/home/r00t-fck# limewire
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from [http://www.java.com](http://www.java.com)
root@r00t-suck-on-that:/home/r00t-fck# 

help . i already install java :(

---

### Post by compengi on 2006-12-07
check out your jave version (~$ java -version) it should be at least 1.4... in order for the limewire to run

---

### Post by swlbc on 2006-12-08
Bravo to whoever contributed the links & code for installing LimeWire using alien .. although it's use is not actually nessessary if you already have the .deb files. but the order an' execution went perfectly for me on a first try ~ I must add, that I've only been using Dapper for under a month so any success has been a real confidence builder.

Thanks again an' hav a pint on a canuk if you're out this way  : )

[email]swlbc2004@yahoo.com[/email]

---

