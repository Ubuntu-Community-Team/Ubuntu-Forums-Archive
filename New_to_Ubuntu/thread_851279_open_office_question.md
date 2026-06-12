---
title: "open office question"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by 1scorpio on 2008-07-06
I was working in open office word processor a few minutes ago and tried to use the data sources function I got an error msg that says "the connection to the data source Evolution local could not be established.
the below that 
The connection to the external data source could not be established. Nodriver was found for the given URL.
where do I find the driver and the connection to the data source 
I need this to create a form

---

### Post by forger on 2008-07-06
Did you setup evolution? Are you using it? Do you have any emails stored?

Install this package:
```
sudo apt-get install openoffice.org-evolution
```
close all openoffice programs and re-run them

---

### Post by forger on 2008-07-06
For the record, the full errors are:
1)The connection to the data source "EvolutionLocal" could not be established.
2)SQL Status: HY000
The connection to the external data source could not be established. No SDBC driver was found for the given URL.
3)A connection for the following URL was requested: sdbc:address:evolution:local

---

### Post by 1scorpio on 2008-07-06
OK did the apt get and got thisReading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  openoffice.org-evolution
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 66.3kB of archives.
After this operation, 340kB of additional disk space will be used.
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main openoffice.org-evolution 1:2.4.1-1ubuntu1
  404 Not Found [IP: 91.189.88.46 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.4.1-1ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.4.1-1ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.46 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by RequinB4 on 2008-07-06
that failed because you didn't have a working internet connection... Is that normal?

---

### Post by 1scorpio on 2008-07-06
I have a working internet connection I can send this

---

### Post by forger on 2008-07-07
change your repository mirror to the main one:
System > administration > software sources > Download from: Main server
click "close" and "reload", wait until it finishes

then try again the command I gave before

If it happens again, post the full output of these commands:
```
uname -a; lsb_release -a
```
(yes, put them in one line)

---

### Post by 1scorpio on 2008-07-07
Linux ubuntuscorpio 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy

---

### Post by forger on 2008-07-07
Weird, it should work, your internet connection looks like it has problems.
You're using i386 ubuntu 8.04, try download this:
[http://mirrors.kernel.org/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.4.0-3ubuntu6_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.4.0-3ubuntu6_i386.deb)
..and double-click the file to install it.

Let's just hope you have the rest of the dependencies.

---

### Post by lilleguard on 2011-03-22
Thanks! Installing openoffice.org-evolution solved the problem immediately!

---

