---
title: "Java Machine Not Found"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by FredJones on 2008-05-05
I am trying to install DbVisualizer ( [http://www.minq.se/products/dbvis/](http://www.minq.se/products/dbvis/) ) on Heron. According to what I see, I have a 1.5 Java Virtual Machine, but the dbv installer doesn't' find it:

```

hershel@ubuntu-hp:~$ java --version
java version "1.5.0"
gij (GNU libgcj) version 4.2.3 (Ubuntu 4.2.3-2ubuntu6)

Copyright (C) 2007 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
hershel@ubuntu-hp:~$ sudo bash ./dbvis_unix_6_0_10.sh
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/hershel/.install4j
hershel@ubuntu-hp:~$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/bin/gij-4.2
 +        2    /usr/lib/jvm/java-gcj/jre/bin/java
          3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

any ideas?

---

### Post by Sinkingships7 on 2008-05-05
```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by FredJones on 2008-05-05
I use aptitude generally, but see what I did. It didn't seem to help. :(

```

fred@ubuntu-hp:~$ sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
[sudo] password for fred: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
fred@ubuntu-hp:~$ sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for sun-java6-plugin
No candidate version found for sun-java6-plugin
The following NEW packages will be installed:
  sun-java6-fonts 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1816B of archives. After unpacking 115kB will be used.
Writing extended state information... Done
Get:1 http://il.archive.ubuntu.com hardy/multiverse sun-java6-fonts 6-06-0ubuntu1 [1816B]
Fetched 1816B in 1s (938B/s)            
Selecting previously deselected package sun-java6-fonts.
(Reading database ... 122795 files and directories currently installed.)
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-06-0ubuntu1_all.deb) ...
Setting up sun-java6-fonts (6-06-0ubuntu1) ...
Updating fontconfig cache for /usr/share/fonts/truetype/ttf-lucida
No CIDSupplement specified for Batang-Bold, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for UMingCN, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Bold, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.

Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
fred@ubuntu-hp:~$ sudo bash ./dbvis_unix_6_0_10.sh
No suitable Java Virtual Machine could be found on your system.
The version of the JVM must be at least 1.5.
Please define INSTALL4J_JAVA_HOME to point to a suitable JVM.
You can also try to delete the JVM cache file /home/fred/.install4j
fred@ubuntu-hp:~$ 

```

---

### Post by kpkeerthi on 2008-05-05
Run ```
sudo update-alternatives --config java
``` and choose Sun's implementation as default.

Edit ./dbvis_unix_6_0_10.sh and add the env variable as below
```
gedit ./dbvis_unix_6_0_10.sh
```
Add the following line to the file. Save & Exit and try again.
```
export INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-6-sun/jre
```

If it fails to find JVM again, try adding / to the end of the line as below 
```
export INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-6-sun/jre**/**
```

---

### Post by FredJones on 2008-05-05
gedit says it doesn't understand the character coding. Quanta says it's a binary and won't edit it. I tried renaming it .txt but that didn't fool EITHER of those apps. So I copied the file to my Windows machine and tried the edits, neither of which worked:

```

fred@ubuntu-hp:~$ sudo bash ./dbvis_unix_6_0_10.sh: command not found.sh: line 2: 
: command not found.sh: line 7: 
: command not found.sh: line 9: 
'/dbvis_unix_6_0_10.sh: line 10: syntax error near unexpected token `{
'/dbvis_unix_6_0_10.sh: line 10: `read_db_entry() {
fred@ubuntu-hp:~$ sudo bash ./dbvis_unix_6_0_10.sh
: command not found.sh: line 2: 
: command not found.sh: line 7: 
: command not found.sh: line 9: 
'/dbvis_unix_6_0_10.sh: line 10: syntax error near unexpected token `{
'/dbvis_unix_6_0_10.sh: line 10: `read_db_entry() {

```

---

### Post by kpkeerthi on 2008-05-05
windows will not run shell commands or bash scripts.

If you are unable to edit dbvis_unix_6_0_10.sh, you can add the export command to .bashrc file in your HOME folder. After adding, close your terminal window and reopen.

---

### Post by FredJones on 2008-05-05
I meant I copied the file to Windows in order to edit it, then I copied it back to Ubuntu to run. It's now edited as u said, but I am still getting the error as noted above. :(

---

### Post by FredJones on 2008-05-05
I tried doing as the installer says:

You can also try to delete the JVM cache file /home/hershel/.install4j

and that did it. AFter that it installed just fine. :)

Thanks

---

