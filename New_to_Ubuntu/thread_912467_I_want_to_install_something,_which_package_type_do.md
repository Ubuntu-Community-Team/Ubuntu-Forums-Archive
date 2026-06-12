---
title: "I want to install something, which package type does ubuntu use?"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-09-06
Which one is it?

.tar.gz
.rpm
YUM

---

### Post by paul101 on 2008-09-06
you can install .debs (easy) or tar.gz's (a bit harder)

---

### Post by Cypher on 2008-09-06
APT and DEBs are what Ubuntu consumes..you can find the package name over at [http://packages.ubuntu.com](http://packages.ubuntu.com). Also, if you know you want a specific command then just enter it at the command line and if it isn't available, Ubuntu will prompt you with the correct package to install to get it..

---

### Post by drs305 on 2008-09-06
The easiest way is to install a package is via the ubuntu repositories and synaptic. Make sure you have the correct repositories enabled (Synaptic, Settings, Repositories). You may have to add extra repositories such as Medibuntu. 

If you can't find a package in synaptic, try to find a .deb package on the internet. Do a search with the name of your app and .deb  Make sure it is for your disto and machine (hardy 64-bit for example). One such place is [http://packages.ubuntu.com.]("http://packages.ubuntu.com.")

If you can't find that, I use an app named 'alien' that converts an .rpm file into a .deb file. You will have to install alien first. Then run: sudo alien -k /path/packagename.rpm to create the deb package. There are many experienced users who will not use alien but prefer to compile the app themselves.

If I have none of those options, you can unzip a .tar.gz file and complile the program yourself. A search of the forums using "make install and ./configure" will show you posts with instructions.

---

### Post by Vivaldi Gloria on 2008-09-06
For installing programs use

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.

---

### Post by aysiu on 2008-09-06
This will tell you how to install software in Ubuntu:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

But given the options you mentioned in the first post, it sounds as if you want to install Flash. The easiest way to do that is to follow the prompts as outlined here:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

