---
title: "ORACLE 10g Standard or Personal Edition on Ubuntu 9.04 or (future) 9.10"
date: 2009-10-09
forum: Programming Talk
---

### Post by daydr3am3r on 2009-10-09
Hi all
First I have to apologise if I'm not posting my question in the right place(this is my first post here).
I an IT Science student. We work on Windows(there is a Microsoft Center in our university) and most of our classes are .NET related. We also have DB classes wich include MS SQL Server, MS ACCESS, MS FoxPro, MySQL and ORACLE. The problem is that I switched to Widows 7 and I need to use ORACLE 10g Standard or Personal Edition (not express). Since ORACLE has not released a version to support Win7 yet I was thinking of installing ORACLE on Ubuntu or openSUSE(since I've been using this two distros for a while now). Also, since I have only 8-9 Gb free on my laptop Ubuntu seamed to be the right decision.
The problem is that ORACLE does not have support for Ubuntu, the only distros supported are RedHat and SUSE Enterprise Edition :mad: 
I know there is another post here:  [http://ubuntuforums.org/showthread.php?t=16654](http://ubuntuforums.org/showthread.php?t=16654)
Also I found this:  [https://help.ubuntu.com/community/Oracle10g](https://help.ubuntu.com/community/Oracle10g)
The question is: did anybody manage to install oracle 10g standard or personal on ubuntu x86 or x64(I prefer x64 though).
Thanks

---

### Post by TheBuzzSaw on 2009-10-10
Good luck on getting Oracle to work. You'll have more success just using MySQL and porting what you can over to Oracle later. :(

---

### Post by daydr3am3r on 2009-10-10
> **TheBuzzSaw said:**
> Good luck on getting Oracle to work. You'll have more success just using MySQL and porting what you can over to Oracle later. :(
Should I declare my self defeated already?:(

---

### Post by goulch on 2009-11-02
Is there any particular reason for using "personal" or "standard" edition and not XE (ie express edition)?  XE installs really easily and works fine with Ubuntu 9.04 (not tried it with 9.10 yet).
Oracle standard & enterprise editions also work fine with Ubuntu 9.04 I have versions of Oracle 10gR2, 11gR1 and 11gR2 all running find in VMs using Ubuntu 9.04. (11gR2 requires minimum 1Gb mem, but other versions run ok with 500Mb).

---

