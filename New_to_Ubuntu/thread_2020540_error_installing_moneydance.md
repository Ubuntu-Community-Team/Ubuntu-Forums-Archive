---
title: "error installing moneydance"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by ryntak on 2012-07-08
I am NEW NEW NEW to linux.  Trying it out to see if I like it better than windows, and I think I might, if I can get some stuff to work...

I tried installing moneydance, and get this error:[INDENT]```
[COLOR=Red][COLOR=Black]Selecting previously unselected package moneydance. 
<snip>
Unpacking moneydance (from /tmp/moneydance.deb) ... 
Setting up moneydance (2011.803) ... 
Preparing JRE ... 
/var/lib/dpkg/info/moneydance.postinst: 
22: /var/lib/dpkg/info/moneydance.postinst: bin/unpack200: not found 
Error unpacking jar files. Aborting. 
dpkg: error processing moneydance (--install): 
subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing:  moneydance[/COLOR][/COLOR]
```[COLOR=Red]
[/COLOR][/INDENT]Any hep is greatly appreciated...

---

### Post by stinkeye on 2012-07-08
According to their support...
> There have been some problems reported with the OpenJDK that now ships with Ubuntu 10.04.

Please try installing the sun jre instead.
I assume it's still the same on 12.04

See this link to install **Oracle** (used to be Sun) **java**.
[**_[COLOR="DarkRed"]Install Oracle Java 7 in Ubuntu via PPA Repository[/COLOR]_**]("http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html")


**[COLOR="Red"]Edit:[/COLOR]** Know nothing about the program and have no money to manage anyway ;)
but as a test installed Oracle Java and downloaded moneydance from their website.
Installed fine and is up and running.

---

