---
title: "What do these commands do?"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by sha1sum on 2013-10-31
I installed Java on Ubuntu, because some application said I needed it. I used this webpage to do it: [http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

I typed the following commands:
```

$ sudo apt-get purge openjdk*
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update 
$ sudo apt-get install oracle-java7-installer 

```

I believe that successfully installed Java. But I'm curious, I'd like to understand a bit more about how Ubuntu works. So my question is: can somebody explain me what those four commands do?

---

### Post by drmrgd on 2013-10-31
Apt-get is the commandline package management system for Ubuntu (and others).  It's pretty big and powerful, and you might have a look at some of the details here:

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

To the commands, the first removes openjdk and all of its config files and such.  Apt-get remove just removes the package, but leaves some residuals.  

The second command 'add-apt-repository' adds a new software repository to your sources.  In this case, it's WebUpd8team's popular Java repository.  

The third command updates the package cache on your system, looking for any upgrades to packages that you have installed, and adding information about the newest version of packages that have not yet been installed.  

The fourth command installs the package 'oracle-java7-installer' to your system.  

You needed to run apt-get update first in order for your package system to see the package that comes from the Webup8team, and then you can install it with the last command.  

Hope that helps!

---

### Post by papibe on 2013-10-31
Hi sha1sum.
```
$ sudo apt-get purge openjdk*
```
Uninstall (if it is install) open source version of Java.
```
$ sudo add-apt-repository ppa:webupd8team/java
```
Add a private/personal repository which in this case contains the latest version of the non free Oracle Java.
```
$ sudo apt-get update 
```
Update your sources so they include the webupd8team repository.
```
$ sudo apt-get install oracle-java7-installer
```
Install oracle-java7-installer from the now available webupd8team repository.

Does that help?
Regards.

---

### Post by sammiev on 2013-10-31
> **sha1sum said:**
> I installed Java on Ubuntu, because some application said I needed it. I used this webpage to do it: [http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

I typed the following commands:
```

$ sudo apt-get purge openjdk*
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update 
$ sudo apt-get install oracle-java7-installer 

```

I believe that successfully installed Java. But I'm curious, I'd like to understand a bit more about how Ubuntu works. So my question is: can somebody explain me what those four commands do?

First you deleted openjdk 
then you added the ppa for Orcale Java which is the java version that works with more programs and website than openjdk
then you updated
then you installed the latest Orcale Java which will update to any newer version updates.

---

### Post by sha1sum on 2013-10-31
Thank you guys. That really helps. Y'all rock

---

### Post by Bashing-om on 2013-10-31
sha1sum; Sure !

"sudo apt-get purge openjdk*" removes all instances of any and all files whose name(s) begins with "openjdk" which is the default open source application to handle java type aps; To prevent conflicts with the "java" that is to be installed.

"sudo add-apt-repository ppa:webupd8team/java" adds a PPA ( Personal Package Archive)to your sources from "webup8team" for their "java".

"sudo apt-get update" refreshes/updates the index/database files on your system, inclusive of the new PPA source that was just added.

 " sudo apt-get install oracle-java7-installer" The package manager goes and hunts up the package "oracle-java7-installer" in relation to the sources and system index files, and then when found, downloads the package, checks the database files (control files) and installs all the needed files in the correct places in accordance with the directives in those data base files. In this case "webupd8team -> "java"

Package management system ->

[INDENT][INDENT]ain't it amaz'n
[/INDENT][/INDENT]

---

### Post by merlyn2748 on 2013-10-31
Do be careful with add-apt-repository. If you don't know and trust the source you can open yourself to malicious software.

---

