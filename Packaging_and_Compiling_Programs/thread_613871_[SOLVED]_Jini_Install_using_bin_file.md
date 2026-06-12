---
title: "[SOLVED] Jini Install using bin file"
date: 2007-11-15
forum: Packaging and Compiling Programs
---

### Post by psavva on 2007-11-15
Hi,


I've been trying to install Jini which is a framework for JavaSpace on Ubuntu Gutsy 7.10

I would really appreciate any help.

```

psavva@Spooky:/usr/src$ sh ./jini2_1.bin 
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-6-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
psavva@Spooky:/usr/src$ 


```

I've tried to reinstall JVM and JDK

---

### Post by epsil00n on 2007-12-04
Hi psawa,
If you still struggle with that, there is complete explanation on the following address:
[http://www.jini.org/wiki/Category:Getting_Started#Linux_Jini_Starter_Kit_installation]("http://www.jini.org/wiki/Category:Getting_Started#Linux_Jini_Starter_Kit_installation")

I used ghex to do the modification and after that the installation was completed successfully. 

Best Regards!

---

### Post by crossdelena on 2008-03-10
Hi,

I am stuck with the same problem...Does anyone has a solution to it??

Thanks,

Cross

---

### Post by psavva on 2008-05-17
I managed to get it working by using IncaX community edition
Check it out. just google incaX
> **crossdelena said:**
> Hi,

I am stuck with the same problem...Does anyone has a solution to it??

Thanks,

Cross

---

### Post by szymon_g on 2008-05-17
> **psavva said:**
> Hi,


I've been trying to install Jini which is a framework for JavaSpace on Ubuntu Gutsy 7.10

I would really appreciate any help.

```

psavva@Spooky:/usr/src$ sh ./jini2_1.bin 
Preparing to install...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libdl.so.2: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/usr/lib/jvm/java-6-sun/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
psavva@Spooky:/usr/src$ 


```

I've tried to reinstall JVM and JDK

did you tried to use a tool 'apt-file' :?
write :

sudo aptitude install apt-file
apt-file update
apt-file search file_of_wanted_so_file

---

