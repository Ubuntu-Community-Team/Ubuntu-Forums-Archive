---
title: "PPA's not there..."
date: 2011-08-19
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-08-19
I am developing 'grubby', a program to apply GRUB2 themes with a minimum effort on end-users' behalf.
Having made myself a launchpad PPA (no easy task, btw), I have problems.

Three things:

1) for the 'install' file under the debian subdirectory, I put 

```
grubby /
```
  
as I believe there are over 200 individual files and they all need to go to different places in the filesystem. I then named the subdirectories of the folder containing the source usr, lib, , share (i.e. .deb package style). Is this the right way to do it? The tutorial I followed said the syntax was to put the path to each individual file, which seemed excessive.

2) Launchpad says there is nothing in my PPA, even thought dput finished without errors. If I run dput again, it tells me there is 'nothing to be done'

3) If I try and add the ppa:

```
Error: can't find signing_key_fingerprint at https://launchpad.net/api/1.0/~michaelrawson76/+archive/grubby

```

Even though I am pretty certain that I've got and published the necessary keys, all with the same email address.

Any ideas, help appreciated. Confused developer now. :confused:

UPDATE: I've just had a rejection from launchpad saying that I mistyped the ppa name, (sorry guys!) however I run dput again with the right PPA and it says that there is nothing to be done.

---

### Post by SevenMachines on 2011-08-20
When you upload to launchpad you get a something_source.ppa.upload file in the something_source.changes/something.dsc directory, you cant upload again when this .ppa file exists so you need to remove it if you need to try again

---

### Post by MG&amp;TL on 2011-08-20
Oh, cool, thanks 7Machines. Will try it now. :)

---

### Post by MadCow108 on 2011-08-20
> **MG&TL said:**
> I am developing 'grubby', a program to apply GRUB2 themes with a minimum effort on end-users' behalf.
Having made myself a launchpad PPA (no easy task, btw), I have problems.

Three things:

1) for the 'install' file under the debian subdirectory, I put 

```
grubby /
```
  
as I believe there are over 200 individual files and they all need to go to different places in the filesystem. I then named the subdirectories of the folder containing the source usr, lib, , share (i.e. .deb package style). Is this the right way to do it? The tutorial I followed said the syntax was to put the path to each individual file, which seemed excessive.



usually your source have should some installation method (e.g. a Makefile) which copies all files to the correct folders with a configurable prefix/destdir.
the install file should only be needed to install something extra from the source or to split your source into several packages.

---

### Post by MG&amp;TL on 2011-08-21
OK...is there a tutorial for that somewhere? Would an install script do, or does it have to be makefile? Sorry, first project, so complete newb to packaging...and how do I put the file locations in the makefile? I've only used the makefile as a compiler aid. :confused:

---

### Post by MadCow108 on 2011-08-22
a script will do too, but sticking to the standard methods is preferable.
If you use a makefile follow the conventions:
[http://www.gnu.org/prep/standards/html_node/Makefile-Conventions.html](http://www.gnu.org/prep/standards/html_node/Makefile-Conventions.html)

higher level tools like, autotools, cmake or scons will usually do everything correct for you.

If its worth the effort depends on your project, if your primary mean of distribution is a self made debian package then what you are doing is ok.
But it will probably not be accepted into any official package repository like that.

---

