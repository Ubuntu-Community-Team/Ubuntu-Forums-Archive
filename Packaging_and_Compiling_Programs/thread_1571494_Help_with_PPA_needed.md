---
title: "Help with PPA needed"
date: 2010-09-09
forum: Packaging and Compiling Programs
---

### Post by akarkor on 2010-09-09
Hallo!
I am a developer of WDT (Web Developer Tools) [http://gnome-look.org/content/show.php/WDT+-+Web+Developer+Tools?content=129726](http://gnome-look.org/content/show.php/WDT+-+Web+Developer+Tools?content=129726)
and my problem is as follow:

I will to open a PPA for WDT on launchpad and I was try 4-5 times to upload all necessary content to launchpad, but always the builds was failed. I am not familiar with this, and I am sure that something is wrong on my side. If I make deb package on my computer everything is fine. I would ask for help, how to prepare everything correctly. I was looked about tons of tutorials, but nothing was helpful. 

Thanks

Peter

---

### Post by SevenMachines on 2010-09-10
If you could post build logs? In general, before uploading to launchpad you should test out the package in a 'clean' environment using pbuilder ( or pbuilder-dist for ease). This gives the best indication of whether or not a build will fail when uploaded. 
Often its a case of missing dependencies in the debian/control file. When you build it these dependencies might be already installed but aren't mentioned in the control file. PBuilder and launchpad etc only install the dependencies you mention explicitly

---

### Post by akarkor on 2010-09-10
Everything is wrong, i am sure that the rules file is wrong. What i need is that all source I have in wdt directory, and this directory need to be moved into /usr/share/ that is all.
So I need create the correct source tarball + correct rules

---

### Post by SevenMachines on 2010-09-10
If you just need to install something without building, cdbs lets you do this quite simply
debian/rules:
> #!/usr/bin/make -f
include /usr/share/cdbs/1/rules/debhelper.mk and then create an install file debian/<mypackagename>.install
Have a look at 'man dh_install' for the format.

---

### Post by SevenMachines on 2010-09-10
Looks like a python thing so you might want to look at
[https://wiki.ubuntu.com/PackagingGuide/Python](https://wiki.ubuntu.com/PackagingGuide/Python)

---

