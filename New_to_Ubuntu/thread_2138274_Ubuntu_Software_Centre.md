---
title: "Ubuntu Software Centre"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by jjhinch on 2013-04-23
When I go onto the Ubuntu Software Centre, I get this message,

"Items cannot be installed or removed until the package catalogue is repaired. do you want to repair it now?". 

I click on repair, enter my password, and then after a few minutes this message comes up,

"Package operation failed.

The installation or removal of a software package failed". 

When I click on "details", it brings up this,

installArchives() failed: dpkg: dependency problems prevent configuration of fgfs-base:
 fgfs-models-base (2.6.0-1~getdeb1) breaks fgfs-base (<< 2.6.0) and is installed.
  Version of fgfs-base to be configured is 2.4.0-1.
dpkg: error processing fgfs-base (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of flightgear:
 flightgear depends on fgfs-base (>= 2.6.0); however:
  Version of fgfs-base on system is 2.4.0-1.
dpkg: error processing flightgear (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 fgfs-base
 flightgear
Error in function: 
dpkg: dependency problems prevent configuration of fgfs-base:
 fgfs-models-base (2.6.0-1~getdeb1) breaks fgfs-base (<< 2.6.0) and is installed.
  Version of fgfs-base to be configured is 2.4.0-1.
dpkg: error processing fgfs-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flightgear:
 flightgear depends on fgfs-base (>= 2.6.0); however:
  Version of fgfs-base on system is 2.4.0-1.
dpkg: error processing flightgear (--configure):
 dependency problems - leaving unconfigured

What do i do to fix this problem? 
Many Thanks

---

### Post by Isamu715 on 2013-04-23
Try the following commands:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
The first one will update package information, the second will try to update the system while smartly resolving dependency problems.
Do you have any third-party repositories enabled?

---

### Post by KnownSyntax on 2013-04-23
If anything just running "sudo apt-get update" should fix these errors, if it doesn't then check your source.list file to make sure that nothing is wrong with it since that could also be the issue as well.

---

### Post by ibjsb4 on 2013-04-23
> **KnownSyntax said:**
> If anything just running "sudo apt-get update" should fix these errors

An update will not fix dependency issues, but it should give you a list of errors to help trouble shoot this.

A dist-upgrade will try to resolve conflicts.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Please post the errors from apt-get update.

---

### Post by jjhinch on 2013-04-23
Thanks,

There is no problem with sudo apt-get update,

However, when I go on to [LEFT][COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get dist-upgrade, I get this message.[/FONT][/COLOR][/LEFT]

hinchliffe@hinchliffe-OEM:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 fgfs-models-base : Breaks: fgfs-base (< 2.6.0) but 2.4.0-1 is installed
 flightgear : Depends: fgfs-base (>= 2.6.0) but 2.4.0-1 is installed
E: Unmet dependencies. Try using -f.
hinchliffe@hinchliffe-OEM:~$ 


Any ideas?

Thanks

---

### Post by Sef on 2013-04-23
> [COLOR=#000000]apt-get -f install[/COLOR]

Try running that command with sudo in front of it.

---

### Post by jjhinch on 2013-04-24
Thanks,

Tried running sudo [COLOR=#000000]*apt-get -f install*[/COLOR], and it this is what it comes up with,

hinchliffe@hinchliffe-OEM:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
hinchliffe@hinchliffe-OEM:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libx264-116 libspatialite2 simgear2.0.0 fgfs-aircraft-base
  libaccess-bridge-java-jni gdebi-core simgear2.4.0 libaccess-bridge-java
  libmusicbrainz4c2a openoffice.org-common libvpx0 packagekit-backend-aptcc
  libiso9660-7 libattica0 fgfs-models-base libid3tag0 libreoffice-l10n-common
  libnvtt2 fgfs-scenery-base libmatroska4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fgfs-base flightgear simgear2.10.0
The following NEW packages will be installed
  simgear2.10.0
The following packages will be upgraded:
  fgfs-base flightgear
2 upgraded, 1 newly installed, 0 to remove and 703 not upgraded.
2 not fully installed or removed.
Need to get 555 MB of archives.
After this operation, 567 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) precise-getdeb/games simgear2.10.0 i386 2.10.0-1~getdeb1 [1,625 kB]
Get:2 [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) precise-getdeb/games flightgear i386 2.10.0-1~getdeb1 [3,904 kB]
Get:3 [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) precise-getdeb/games fgfs-base all 2.10.0-1~getdeb1 [550 MB]
Fetched 555 MB in 24min 44s (374 kB/s)                                                                          
Selecting previously unselected package simgear2.10.0.
(Reading database ... 493463 files and directories currently installed.)
Unpacking simgear2.10.0 (from .../simgear2.10.0_2.10.0-1~getdeb1_i386.deb) ...
Setting up simgear2.10.0 (2.10.0-1~getdeb1) ...
dpkg: dependency problems prevent configuration of fgfs-base:
 fgfs-models-base (2.6.0-1~getdeb1) breaks fgfs-base (<< 2.6.0) and is installed.
  Version of fgfs-base to be configured is 2.4.0-1.
dpkg: error processing fgfs-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of flightgear:
 flightgear depends on fgfs-base (>= 2.6.0); however:
  Version of fgfs-base on system is 2.4.0-1.
dpkg: error processing flightgear (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                       ldconfig deferred processing now taking place
Errors were encountered while processing:
 fgfs-base
 flightgear
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now what do I do?

Thanks

---

### Post by Paqman on 2013-04-24
Try it again but with sudo in front of it:
```

sudo apt-get -f install

```
You always need sudo for any commands to install, remove or update packages. This is what stops dodgy things from the internet sneaking malware onto your machine.

---

### Post by jjhinch on 2013-04-24
Tried again, Same message.

I would be willing to uninstall flightgear and fgfs if it would solve the problem, and if i was given the terminial command

Thanks

---

### Post by ibjsb4 on 2013-04-24
Try this in terminal

```
sudo apt-get remove --purge flightgear fgfs-base
```

---

### Post by jjhinch on 2013-04-24
Thank You Very Much

sudo apt-get remove --purge flightgear fgfs-base
Sorted out the problem

Thanks everybody

---

### Post by ibjsb4 on 2013-04-24
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

