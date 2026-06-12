---
title: "compiling aufs"
date: 2007-11-12
forum: Packaging and Compiling Programs
---

### Post by apocalip on 2007-11-12
Hello!

i've been searching and trying to find/compile the unionfs alternative for my gusty but i'm not able to.

Could someone please give me a hint into the right direction how to do this?

Greetz apocalip

---

### Post by MrFSL on 2007-11-12
Well the homapage seems to be located here:
[http://www.fsl.cs.sunysb.edu/project-unionfs.html](http://www.fsl.cs.sunysb.edu/project-unionfs.html)
or
[http://www.filesystems.org/project-unionfs.html](http://www.filesystems.org/project-unionfs.html)
 -  has tutorials and examples.

Furthermore, 'apt-cache search unionfs' (in Feisty) yields:
```
fsl@Laptop:~$ apt-cache search unionfs
unionfs-source - Source for the union filesystem
unionfs-tools - Tools to manage unionfs filesystems
unionfs-utils - Transition package for unionfs-tools rename
fsl@Laptop:~$
```

Although I haven't tried it I would think that you might want to start by installing the build dependencies... something like:
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install unionfs-source unionfs-utils build-essential
sudo apt-get build-dep unionfs
... 
```

Then try building again.

According to their homepage their might already be some support in Gutsy. Is it listed in:
```
cat /proc/filesystems
```?

---

### Post by steync4 on 2007-12-12
I've also been looking into aufs as an alternate to unionfs.

My main problem is that i can create a union, but when i try to share it with Samba some of the directories gets lost.

Ubuntu has the source for aufs, but as far as i know no precompiled kernel modules exist, and no clear info on how to compile it for 7.10 is out there either.

---

