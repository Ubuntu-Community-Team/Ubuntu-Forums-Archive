---
title: "Issues trying to install WINE!"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by Soriano on 2008-11-02
Hey all,

I'm brand new to linux and loving it so far.  I just upgraded from 8.04 to 8.1 without a hitch.

However today I went to install Wine onto my machine. Here is what I did in the terminal:

[B]matthew@hpdv9000:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  binfmt-support wine
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/7528kB of archives.
After this operation, 56.0MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labeled
 'Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081028)'
in the drive '/cdrom/' and press enter[/B]

I'm not exactly sure what is going on and why it is asking for the install disk.  This didn't happen under 8.04 so some setting must have changed.  Any help much appreciated!!!!:)

---

### Post by perlluver on 2008-11-02
Go to System>Administration>Software Sources, and turn off the CD.

---

### Post by Soriano on 2008-11-02
Wow what a simple fix!  Won't forget that again!

Thanks!

---

