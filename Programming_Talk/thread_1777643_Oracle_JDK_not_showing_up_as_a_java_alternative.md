---
title: "Oracle JDK not showing up as a java alternative"
date: 2011-06-08
forum: Programming Talk
---

### Post by anthony-bartoli on 2011-06-08
I just installed Oracle's [Java SE 6 JDK]("http://www.oracle.com/technetwork/java/javase/downloads/jdk-6u26-download-400750.html"). 

After running ```
./jdk-6u26-linux-i586.bin
``` terminal says that it has been successfully installed. 

However, when I run ```
update-java-alternatives -l
``` I don't see the newly installed JDK. I only see the OpenJDK (what I installed awhile back). 

What are the possible reasons I'm unable to see and use Oracle's JDK?

---

### Post by SevenMachines on 2011-06-08
the alternatives system is set up by the java repository packages on install and removed on uninstall (see for example /var/lib/dpkg/info/openjdk-6-jdk.postinst and .prerm). In other words, its done by the debian packaging and seemingly the binary installer from sun doesn't do it itself. You can update alternatives manually ( see 'man update-alternatives') if you want. you could probably pull out a little script from the packaging scripts mentioned above

---

### Post by t1497f35 on 2011-06-08
Not a rant, but it's time for Oracle to realize that debian/Ubuntu is far more popular (on desktops - which is what Java devs use to create all types of Java apps) than RPM distros, by now they should ship the JREs/JDKs as .debs as well.

---

### Post by SevenMachines on 2011-06-08
Not to defend Oracle in that (a) It wasn't them that packaged them, and (b) I dont want to :) but, sun java 6 packages are available from the 'partner' repositories in ubuntu. Generally i'd say use openjdk unless you have a specific reason to use sun java, in theory you shouldnt, in practice there can be...

---

### Post by t1497f35 on 2011-06-08
To me openjdk is certainly a lot more usable than it was a few years ago, but to me it's still slightly weird and buggy.
Also, Ubuntu rarely (if at all) updates their java stack to a new version within the same Ubuntu release. For instance on Maverick it's still 6.24, probably same version is on Natty, and that's while Oracle already shipped 2 updates. Same  is true for NetBeans and VirtualBox. So I'd rather fetch the latest .deb version from Oracle rather than hope that in several months it will be updated in Ubuntu (if at all).

---

### Post by stchman on 2011-06-09
Enable the Partner Repository and install Sun/Oracle Java.

---

