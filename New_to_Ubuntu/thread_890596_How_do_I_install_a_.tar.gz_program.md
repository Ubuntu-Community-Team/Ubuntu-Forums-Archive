---
title: "How do I install a .tar.gz program"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by arashiko28 on 2008-08-15
I want to install a .tar.gz program, in this particular case, clamav-0.93.3.tar.gz

There is an easy way not IT intended instructions to do so?:confused:

BTW i already checked google for a .deb or .rpm package, there's none.:(

Please be kind...

---

### Post by Pro-reason on 2008-08-15
Version 0.92.1 of clamav is in the repositories.  Is your point that you really want a later version?  I don't think viruses are a problematic enough issue on Linux for that to be necessary.

If you really need to install from a tarball, then decompress it.  Then look inside.  There is usually a readme file with instructions.  If the tarball contains source code, you generally have to configure it by typing "./configure", then compile it by typing "make", then install it by typing "sudo make install".  That's a generalisation.  Always read the documentation.

---

### Post by hansdown on 2008-08-15
Hi arashiko. This should help.  [http://ubuntuforums.org/showthread.php?t=540961](http://ubuntuforums.org/showthread.php?t=540961)

---

### Post by overdrank on 2008-08-15
> **arashiko28 said:**
> I want to install a .tar.gz program, in this particular case, clamav-0.93.3.tar.gz

There is an easy way not IT intended instructions to do so?:confused:

BTW i already checked google for a .deb or .rpm package, there's none.:(

Please be kind...

Hi and if you are using Hardy you can install clam via add and remove located under applications. 
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
To slow :)

---

### Post by Troll_the_Great on 2008-08-15
Here's another link for compiling from source:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
Cheers!

---

### Post by ggaaron on 2008-08-15
If you really need the later version you'll need to install some additional programs (GCC for example) and a lot of *-dev packages, I'd recommend to use provided version - automatic updates, easy removal and of course easy installation.

---

### Post by arashiko28 on 2008-08-15
I want the later version, I don't use clamAV as a linux antivirus, but to protect my USB drives from staying infected when I connect them to a windows computer. This readme file is pretty useless :confused: that's why I asked.

---

### Post by MonctonJohn on 2008-08-15
Compiling isn't for everone. Check the changelog for the differences in the two versions to see if its worth compiling the new version.

The readme probably has generic instructions like configure, make, and make install just like Pro-reason said. What it doesn't tell you is that if you have any missing dependencies your configure will fail. That's one of the reasons behind a package manager to install the dependencies along with the desired software.

I've gone through this thousands of times on Slackware where I compiled everything and trust me, dependencies are hell.

---

### Post by fiddler616 on 2008-08-15
I'm looking forward to reading this...
*bump*

---

### Post by Valino on 2008-08-15
I think that this link may be useful: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by t0p on 2008-08-15
> **Pro-reason said:**
> 
If you really need to install from a tarball, then decompress it.  Then look inside.  There is usually a readme file with instructions.  If the tarball contains source code, you generally have to configure it by typing "./configure", then compile it by typing "make", then install it by typing "sudo make install".  That's a generalisation.  Always read the documentation.

Pro-reason's advice summarizes the process pretty well.  But you will need the package **build-essential** installed in order to compile source.  So the first thing to do is to type into terminal
```
sudo apt-get install build-essential
```

---

### Post by arashiko28 on 2008-08-15
> **Valino said:**
> I think that this link may be useful: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

> configure: error: C compiler cannot create executables


:confused:

I think this is way too advanced for me, I'm just a med student that got freakin' tired of dealing with winblows and viruses...

I'll stay with my version that is 0.92.1

---

### Post by Paqman on 2008-08-15
> **arashiko28 said:**
> 
I'll stay with my version that is 0.92.1

Using properly packaged software from the repos is always the best idea. Compiling from source breaks the dependency system and can therefore lead to instability.

---

### Post by Vined Adobo on 2009-07-31
I'm trying to install clamav-0.95.2 because the clamtk gui complains that the av engine is out of date.  The instructions in the INSATLL file (a readme file) tells me to cd to the folder/directory where the source files are.  The trouble is that almost all of the folders/directories contain .c and .h files.  My understanding is that .c are source code and .h files are header files.  Which directory to I use ./configure on?  All of them, and then make and install each one?  I'm lost.  Someone please give me some hints.
Thanks,

Dave

---

### Post by Liolikas on 2009-07-31
Forget it fill bug "clamgtk complains that the av engine is out of date" in:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

You should get new with updates later. Install everything only trough package manager or apt-get and *.deb as last resort. Last last resort convert *.rpm to *.deb.

---

### Post by Vined Adobo on 2009-07-31
> **Liolikas said:**
> Forget it fill bug "clamgtk complains that the av engine is out of date" in:
[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)

You should get new with updates later. Install everything only trough package manager or apt-get and *.deb as last resort. Last last resort convert *.rpm to *.deb.

Thank you.  I'll do that.
Dave

---

### Post by kansasnoob on 2009-07-31
You can use the clamav ppa:

[https://launchpad.net/~ubuntu-clamav/+archive/ppa](https://launchpad.net/~ubuntu-clamav/+archive/ppa)

Much easier than tarball.

---

