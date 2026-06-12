---
title: "Compile and install from source with ease!"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by maup on 2008-07-04
Hi,

I have written a couple of scripts which makes it easier to install and maintain programs from source. The concept is stolen and adapted from the GoboLinux and Stow projects. 
Please try it out and give some feedback. 

[http://linuxconfig.dyndns.org:1184/lazy/LazyLinuxWiki/Gnuppix/Introduction](http://linuxconfig.dyndns.org:1184/lazy/LazyLinuxWiki/Gnuppix/Introduction)

---

### Post by nowshining on 2008-07-04
how hard is it to install? ur usage instructions makes it more work than

./configure
make
sudo checkinstall -D make install

---

### Post by maup on 2008-07-07
It is actually more of a software distribution system with a lot of flexibility. I tried to combine the best from Gentoo, GoboLinux, Slackware and plain old "compile from source" to something that I would want to use myself. I got tired of doing the same thing over and over again, trying to remember how a program should be optimally compiled and installed. I also needed a way to quickly move/reinstall a program to another system.
Last bot not least, I wanted a flexible system which can do all the small 'special tweaks' which are so often needed. The scripts can be totally adapted and rewritten for a specific program since the scripts and program are distributed together.

---

### Post by nowshining on 2008-07-09
why not just download the source and compile from the main program site?

---

### Post by llamakc on 2008-07-09
Or why not use the functionality that is already built into dpkg?

---

### Post by maup on 2008-07-10
> **llamakc said:**
> Or why not use the functionality that is already built into dpkg?

I don't want to use a package manager. The filesystem should be the "package manager" where each program has it's own directory.
Secondly, I want a system which is focused on the applications, not the package manager or a specific distribution.
To nowshining, the scripts do download the source from the "main program site". I don't propose any kind of mirror repository.

---

### Post by nowshining on 2008-07-10
what would be great is a script that would do ./configure, if there are any errors, check to see if the lib-dev versions are in the repos, download them, then do make, and ask whether to do make install or use checkinstall, etc... from there it prob. would have to be done manually, etc..

as for the dpkg thing, i agree - and builiding from source from dpkg requires the source files to be downloaded from the ubuntu site, and won't check dependencies for non ubuntu apps in the system.

---

### Post by maup on 2008-07-13
> **nowshining said:**
> what would be great is a script that would do ./configure, if there are any errors, check to see if the lib-dev versions are in the repos, download them, then do make, and ask whether to do make install or use checkinstall, etc... from there it prob. would have to be done manually, etc..

I don't think that dependencys should be handled automagically. What could be done is to include the buildscripts for some important deps in the buildscript for the actual application. Perhaps in archive/depends..

---

### Post by nowshining on 2008-07-13
those devs are only needed for building the programs - :)

---

### Post by maup on 2008-07-15
> **llamakc said:**
> Or why not use the functionality that is already built into dpkg?

Just wanted to add some more comments to my previous reply..

dpkg is just too much for my brain. I only want to share what I think is a good idea. 
With Gnuppix it's really simple to move a working and configured program from one system to another, just copy the directory where the program is located and off you go. 
No need to keep a copy of a .deb package which has to be reconfigured and fought with all over again.
It's also easy to have several versions of the same program installed at the same time. Don't try that with dpkg.. [-X
I have used this concept with great success, even with the Linux kernel. The flexibility to tailor a program to your specific needs, combined with simplicity and the possibility to distribute the build scripts with or without the program itself, these are the key selling factors! \\:D/

Gnuppix is a simple system which can be made very complex but still simple. I think <insert your favorite package manager> is a complex and complicated system which doesn't scale very well.

---

### Post by nowshining on 2008-07-15
oh i agree apt-get and, etc.. sucks and u start to have problems when installing certain libs from vanilla sources.

---

