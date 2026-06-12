---
title: "Open Office Base JRE issue"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Xoanan on 2008-05-05
Hi All

I have been having trouble installing Java onto OO Base lately.  I keep adding it and it doesn't seem to like it much.  I have uninstalled and reinstalled Java to no avail. Here are some pix that describe it

[IMG]http://ubuntuforums.org/album.php?albumid=34&pictureid=294[/IMG]

Then I attempt to install java

[IMG]http://ubuntuforums.org/picture.php?albumid=34&pictureid=295[/IMG]

Then I close base and reopen it only to get the same error message. Then I go into tools -> options ->  open office.org -> java and I see that none of them are selected.  I must be missing something, but what?

[IMG]http://ubuntuforums.org/picture.php?albumid=34&pictureid=296[/IMG]

---

### Post by Xoanan on 2008-05-06
I discovered something through reading some threads here.
Java 6 is on the machine but it is not running.

Here is etc/jvm

```
 This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr
```

I try to install java 6 and get this

```
xoanan@ubuntu:/$ sudo apt-get install sun-java6-bin sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
sun-java6-jre set to manually installed.
The following packages were automatically installed and are no longer required:
  libflashsupport linux-headers-2.6.24-16-generic linux-headers-2.6.24-16
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-doc (6-06-0ubuntu1) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```
I have downloaded the documentation, but still no luck
:confused:

---

### Post by Xoanan on 2008-05-07
Reported on launchpad

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/227679]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/227679")

---

### Post by jimv on 2008-05-07
Did you try to install sun-java6-doc?  because you need sun-java6-jre

---

### Post by Xoanan on 2008-05-07
Yep; several times in fact; I even uninstalled and reinstalled java common, and Open Office.  Nada.

---

### Post by Xoanan on 2008-05-08
Found a fix on launchpad; apparently, with the release of Hardy, the file home/openoffice.org2/usr/config/javasettings_linux_x86.xml leaves java disabled, so you have to delete that and reboot so that open office creates it again. It worked!
:popcorn:

Thanx for the assist!

---

