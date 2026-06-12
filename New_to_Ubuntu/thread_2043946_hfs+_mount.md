---
title: "hfs+ mount"
date: 2012-08-17
forum: New to Ubuntu
---

### Post by jlne on 2012-08-17
Hello. I am using Ubuntu server 12.04. I have a 3Tb USB drive. I have installed hfsprogs, hfsplus, and hfsutils. I am using gparted v0.11.

I am creating just one primary hfs+ partition on the drive. HFS+ is needed because the drive will store central media files for a time and then go offsite with a Macintosh. However, I get a warning and am unable to mount the drive. 

Warning:
Unable to read the contents of this file system!
Because of this some operations may be unavailable.
The cause might be a missing software package. The following list of software packages is required for hfs+ file system support: hfsprogs.

dmesg |tail reports:
hfs: invalid secondary volume header
hfs: unable to find  HFS+ superblock

What am I doing wrong, and what to I need to do in order to correct this?

Thank you!

---

### Post by gordintoronto on 2012-08-17
The error message suggests you have not actually installed hfsprogs.

Is there some reason you want to use Ubuntu Server? It's good for running a high-volume web site, but it's not very user-friendly. Ubuntu Desktop is very slightly lower performance, but it's a lot easier to use.

---

### Post by jlne on 2012-08-22
According to what I've read so far, I have hfsprogs installed. 

**dpkg -l | grep hfs** produces:

ii  hfsplus                                1.0.4-12build3
     Tools to access HFS+ formatted volumes
ii  hfsprogs                               332.25-10
      mkfs and fsck for HFS and HFS+ file systems
ii  hfsutils                               3.2.6-11build3
     Tools for reading and writing Macintosh volumes
ii  hfsutils-tcltk                         3.2.6-11build3
     Tcl/Tk interfaces for reading and writing Macintosh volumes
ii  libhfsp0                               1.0.4-12build3
     Shared library to access HFS+ formatted volumes

I formatted the drives on a Mac and turned of journaling and I get the same error message, so it is independent of configuration source.

I am using server simply because I needed some file sharing and web resources. This is my first time with Unix in something like 15 years so my knowledge base is rudimentary now. They are already set up and in use so I would rather not change them.

Cheers!

---

### Post by jlne on 2012-08-23
As an addendum to the previous post:

Ubuntu 12.04 will not mount the partition due to the errors mentioned previously. However, when I run fsck.hfsplus I get the response that the volume appears to be OK.

I am stumped.

---

### Post by RazorD on 2012-08-26
I've got this issue too (Though, i'm on debian sid)

Lots of cases of this over the years on google, but nothing recent that sheds any light. I'm guessing its a bug in the HFS modules.

Edit: I updated my kernel and it fixed the problem.

---

