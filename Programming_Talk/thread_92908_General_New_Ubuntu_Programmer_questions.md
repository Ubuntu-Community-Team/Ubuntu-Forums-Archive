---
title: "General New Ubuntu Programmer questions"
date: 2005-11-20
forum: Programming Talk
---

### Post by dogen on 2005-11-20
Let's say you want to install a programming environment on your computer... What's best, to go to the language website (like python.org) and find the download or to look for the apt-get equivalent for Ubuntu?

And let's say you download a programming package, like ruby-1.8.3.tar.gz - where's a good place to stuff it? (no obscene responses please)    /etc?  /usr? my home directory?

thanks for any tips

---

### Post by ofek on 2005-11-20
Its the eziest and probably the best idea to install the .deb package from synaptic(if possible).
I personally install program not from synaptics on /home/username/bin/ .
For 90% of my programing I use bluefish great editor for any language or atleast all of which I use (pascal,c,c++,java,html,python). you can install it through synaptics.

---

### Post by toojays on 2005-11-21
Most of the stuff you will want is available via the synaptic package manager. This is the best way to install a new programming environment in Ubuntu.

---

### Post by Roptaty on 2005-11-21
If you however can't find the debpackage you are looking for in Synaptic (very seldom), you might want to download, compile and install the program using a tarball/tar.bz2 for yourself. In this case, use /usr/local for installation. This is btw the standard location for customcompiled packages. 

If you install to /usr, you may overwrite files from installed deb packages.

---

