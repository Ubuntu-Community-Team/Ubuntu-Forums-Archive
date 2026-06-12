---
title: "apt-get source and edit-patch for a specific unreleased version"
date: 2011-09-01
forum: Packaging and Compiling Programs
---

### Post by esdi on 2011-09-01
Hello, 

I found a bug and reported it on launchpad without a patch file attachment (Bug #[838720]("https://bugs.launchpad.net/ubuntu/+source/iso-scan/+bug/838720")).
I seem to have difficulty creating a patch for the upcoming Oneiric version of the package.

looking at [https://wiki.ubuntu.com/PackagingGuide/Complete#Authoring_a_patch](https://wiki.ubuntu.com/PackagingGuide/Complete#Authoring_a_patch)
I think I am supposed to do:

```
$ LC_ALL=C apt-get source iso-scan
$ cd iso-scan-1.35ubuntu1
$ edit-patch patch-for-folder-with-spaces
```Unfortunately, I have some problems with these commands

**Issue 1)**
```
$ LC_ALL=C apt-get source iso-scan
```retrieves version 1.31 and i need the source for version 1.35
I also tried
```
$ LC_ALL=C apt-get source iso-scan=1.35
$ LC_ALL=C apt-get source iso-scan=1.35ubuntu1
```but the packages can not be found
I suppose I am not using the correct synthax or do not have the proper software sources enabled for Oneiric development

**Issue 2)**
For the fun of it, I tried to patch version 1.31 to see what the patching interface looks like and what files it generates
again i can't seem to get it working.
I get "No patchsystem detected, cannot create new patch (no dpatch/quilt/cdbs?)" when executing the edit-patch program
I installed both dpatch and quilt pachages but I canot find the package that installs the cdbs program
How can I get edit-patch working?

Thanks, 
Sylvain

---

### Post by Bachstelze on 2011-09-01
To get the oneiric version:

```
pull-lp-source iso-scan oneiric
```

The package currently does not have patches, so edit-patch won't work, you'll have to create a patch from scratch.

---

### Post by esdi on 2011-09-01
Thanks, 
I got the source and will look into creating a new patch (I thought this is what edit-patch was supposed to help me do)

I also found the cdbs package, 
I must have typed it wrong the first time :-\"

Regards,  
Sylvain

---

