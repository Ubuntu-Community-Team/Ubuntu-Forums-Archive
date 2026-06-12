---
title: "How to make a Debian package of shell scripts?"
date: 2010-07-27
forum: Packaging and Compiling Programs
---

### Post by &#35874;&#32487;&#38647; on 2010-07-27
Hi, I'm newbie on Ubuntu/Debian packaging. 

For those autoconf/automake projects, how debhelper knows the directory layout the project would installed to? Does it look into and analyse the configure.in/Makefile.in files? 

If my project contains only some shell scripts, which needn't be built with GNU Make, how to package it into .deb? And what's the convention on the directory structure in the .deb? 

For autoconf, user can specify the prefix by configure --prefix=/xxx, my project doesn't use autoconf, should I provide a configure as well?

---

### Post by SevenMachines on 2010-07-28
> **&#35874 said:**
> 
For those autoconf/automake projects, how debhelper knows the directory layout the project would installed to? Does it look into and analyse the configure.in/Makefile.in files? 

probably better explanations than my ramblings can be found looking at the man pages of dh_auto_configure, dh_auto_build and dh_auto_install. they try and intelligently use ./configure, make, make install.

> 
If my project contains only some shell scripts, which needn't be built with GNU Make, how to package it into .deb?  see[ https://wiki.ubuntu.com/PackagingGuide/Complete#rules]("https://wiki.ubuntu.com/PackagingGuide/Complete#rules")
the default rules file created by dh_make should be fine, it runs a whole bunch of debhelper tools but wont try to build something if it doesnt find some sort of makefile or something like that. 
                                
you can then create a debian/<packagename>.install file that just installs the files to the right places.
see 
$ man dh_install
for an explanation and the format of the file

---

