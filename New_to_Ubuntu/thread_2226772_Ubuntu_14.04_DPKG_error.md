---
title: "Ubuntu 14.04 DPKG error"
date: 2014-05-28
forum: New to Ubuntu
---

### Post by Thechromester420 on 2014-05-28
Hello trusty 'Buntu forumers!
Recently, I've been getting an error related to DPKG.
For the example I'm about to show you, I'm showing the results of trying to use apt-get install (apt-get upgrade is flipping out as well) to install Ninvaders.

```
sudo apt-get install ninvaders
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  ninvaders
0 upgraded, 1 newly installed, 0 to remove and 52 not upgraded.
Need to get 0 B/16.3 kB of archives.
After this operation, 102 kB of additional disk space will be used.
Selecting previously unselected package ninvaders.
dpkg: warning: files list file for package 'python-markupsafe' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `python-gobject-2': No such device or address
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

Apparently something is wrong with Python? Python is installed and functional at version 3.4, if that helps.
Need help as soon as possible, Certain things I need to do have been crippled by this.

---

### Post by ian-weisser on 2014-05-29
The dpkg database seems to have been corrupted.

Try:
```
sudo apt-get install --reinstall python-markupsafe python-gobject-2
```

Reinstallation of the affected packages will usually fix the database.

---

### Post by Thechromester420 on 2014-05-29
Thank you! I will see how this works in a few minutes, I'm currently busy with some stuff right now.

---

### Post by Thechromester420 on 2014-05-30
Here are the results.
```
sudo apt-get install --reinstall python-markupsafe python-gobject-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 52 not upgraded.
Need to get 0 B/180 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: warning: files list file for package 'python-markupsafe' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 unable to open files list file for package `python-gobject-2': No such device or address
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by ian-weisser on 2014-05-30
Okay, we'll get out the spanner and elbow grease.

Test to see if the python-markupsafe.list file exists, and it's size. While we're at it, let's see what dpkg can tell us about the package state.
```
$ ls -l /var/lib/dpkg/info/python-markupsafe.list
-rw-r--r-- 1 root root 1661 Oct 16  2013 /var/lib/dpkg/info/python-markupsafe.list

$ dpkg -l python-markupsafe
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python-markups 0.15-1build3 i386         XML/HTML/XHTML Markup safe string

```
In this example, it exists, is owned by root, and takes up 1661 bytes of disk space.
Dpkg says it should be installed, is actually installed, no errors.

---

### Post by Thechromester420 on 2014-05-30
Err... Is this a bad thing?:
```
$ ls -l /var/lib/dpkg/info/python-markupsafe.list
ls: cannot access /var/lib/dpkg/info/python-markupsafe.list: No such file or directory


```

---

### Post by Thechromester420 on 2014-05-30
As for the DPKG check:

```
$ dpkg -l python-markupsafe
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python-markups 0.18-1build2 i386   

```

---

### Post by Thechromester420 on 2014-05-31
Due to an accident when live-machine testing BootCD's, I have found teh need to re-install Ubuntu on a more suitable data container. (18 gb of space to 233 gb of space. flash drive to hard drive) But now I have the need to discover how to install the Gnome-Flashback mode.

---

