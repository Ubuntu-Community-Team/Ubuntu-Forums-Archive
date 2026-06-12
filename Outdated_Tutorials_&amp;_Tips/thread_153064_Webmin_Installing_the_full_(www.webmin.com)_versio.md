---
title: "Webmin: Installing the full (www.webmin.com) version"
date: 2006-03-31
forum: Outdated Tutorials &amp; Tips
---

### Post by lindsay_keir on 2006-03-31
Webmin: Installing the full ([www.webmin.com](www.webmin.com)) version

This describes how I installed the full ([www.webmin.com](www.webmin.com)) version of Webmin. The trick is to "fool" Debian. I use [k]Ubuntu - there should not be any differences from Debian.

(1) Install only these two packages, WITH their automatic dependencies
[LIST]
[*][FONT="Fixedsys"]**sudo apt-get install webmin webmin-core**[/FONT]
[/LIST]

(2) Use Synaptic and LOCK these two packages.
[LIST]
[*]Select **webmin**      and Package > Lock Version
[*]Select **webmin-core** and Package > Lock Version
[/LIST]

Now all libraries, etc. are setup the Debian way, and never again updated....

(3) Change Webmin so root can use Webmin - it's really too important not to use root.
    [LIST]
[*][FONT="Fixedsys"]**sudo /usr/share/webmin/changepass.pl /etc/webmin root password**[/FONT]
[/LIST]

(4) Login to Webmin [https://localhost:10000](https://localhost:10000) using User: root and root's password

**[SIZE="3"]Webmin Configuration...[/SIZE]**

(5) Operating System 
[LIST]
[*]Should be already set to Debian from the install.
[/LIST]

(6) Authentication 
[LIST]
[*]Auto-logout after [30] minutes of inactivity
[/LIST]

(7) IP Access Control - from localhost, all locally connected PCs, and wherever else...
[FONT="Fixedsys"] 
     127.0.0.1
     192.168.1.0/255.255.255.128
[/FONT]

**Upgrade Webmin**
    (*) Latest version from [www.webmin.com](www.webmin.com)

[SIZE="3"]**You're done!**[/SIZE]

(1) I recommend using the theme: **stressfree** - especially if Clustering

(2) I also install the modules...
[LIST]
[*]text-editor
[*]neisysinfo
[*]sysinfo0.2.5c
[*]sysinfo-1.170
[*]nettools-1.060.1
[/LIST]

(3) After defining Servers, Clusters - ensure the O/S is Debian!!! 
    - This is IMPORTANT; the correct O/S must be named!

---

### Post by spherethree on 2006-04-22
I have Ubuntu Breezy and it doesnt work for me.  

spherethree@computer:~$ sudo apt-get install webmin webmin-core
Reading package lists... Done
Building dependency tree... Done
Package webmin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package webmin has no installation candidate

---

### Post by adamkane on 2006-04-22
The webmin available from the Ubuntu repositories is old and incomplete. Better off installing the latest webmin from source. There is already a howto for this.

What's needed is a howto to enable all the webmin modules for Ubuntu.

---

### Post by Seb Spiers on 2007-08-23
> **adamkane said:**
> The webmin available from the Ubuntu repositories is old and incomplete. Better off installing the latest webmin from source. There is already a howto for this.

What's needed is a howto to enable all the webmin modules for Ubuntu.Can you link me? :X

---

