---
title: "Java Runtime Environment(JRE)"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by huwaw69 on 2008-11-04
i installed frostwire on my ubuntu intrepid...
i opened frost wire on terminal...

HOSTNAME IS ubuntu
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: cannot access /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

so i have updated my java in [www.java.com](www.java.com)...
so it is now updated.. but the problem is...
when i open frostwire again in terminal it says that again...
i have restarted my laptop.. Still the same...

when i try to find what version of java i have on the terminal

java version "1.5.0"
gij (GNU libgcj) version 4.3.2

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


but on java.com website my java is updated to 1.6.something..

What seems to be my problem? and what should i do... im just new to linux and ubuntu.. so please don't post some complicated instructions please...


:guitar:

---

### Post by taurus on 2008-11-04
What does it say when you run this command from a terminal?

```
java -version
```
You need Sun's java to run frostwire and you can install it with

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
java -version
```

---

### Post by huwaw69 on 2008-11-04
huwaw69@ubuntu:~$ sudo apt-get install sun-java-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java-bin


That what it says and it asks me if im a root... w/c i dont know how to be a root

---

### Post by taurus on 2008-11-04
You need to look at what you just typed and my command.  You missed a **6**.

---

### Post by huwaw69 on 2008-11-04
sori my bad...
ok type again...

huwaw69@ubuntu:~$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  gnustep-base-common libportaudio2 gnustep-gui-common gnustep-common
  libffcall1 gnustep-back-common libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

huwaw69@ubuntu:~$ java -version
java version "1.5.0"
gij (GNU libgcj) version 4.3.2

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.


Still the same ...  any alternatives?

---

### Post by gandaran on 2008-11-04
you provably have other java versions installed like sun java 1.5 or open java, it's best you remove all except sun java6
open synaptic and search for java, mark for complete removal all open java and sun-java5, leave the sun-java6 installed
if you installed the sun-java from  [www.java.com](www.java.com) you'll have to delete those files, you won't be able to remove it in synaptic.

---

### Post by huwaw69 on 2008-11-04
Hahahah GOTCHA! thanks to you guys! ive solved the mystery.. hahaha
I opened synaptics the type java and in the bottom right i clicked status
Then completly removed all the JAVA jre's i dont remember all but it has the java-gcj-compat-headless i think...

So if someone reding this has a problem same as mine... there you go! Just read

---

