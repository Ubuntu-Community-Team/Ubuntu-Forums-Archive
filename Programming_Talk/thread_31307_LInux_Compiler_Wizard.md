---
title: "LInux Compiler Wizard"
date: 2005-05-02
forum: Programming Talk
---

### Post by COBRA 8288 on 2005-05-02
is this feasible? I know little about command lines and code, plus i havent used the compiler tool as of yet.....but if Linux is to be "ready"
for the masses, then the community is somehow going to have to "unify" the download and installation process. it would be nice just to download a single version of a software app and simply run an installation wizard. I fell this should be the goal of linux programmers out there..... while maintaining  the freedom that the terminal brings to linux..  how hard would it be to write a scripting prigram to automate the installation process for compiler? a few commands for 
compiling configuration.... a few commmands for creating a execution icon on the start menu......and if needs be,...... a very simple to use, distro exception commands database that you could easily download  one file with every known linux app....(not sure you need distro specific commands for compiler........and if so
either unite the commands of all distros, or have a very easy to use update thingy NO COMMANDS NEEDED..............

well i would be intersted in your opinions about this , and your own ideas or information about the push for "mouse click  installation".

                   thank you,
                                COBRA 8288

---

### Post by -Rick- on 2005-05-02
Its already done for linux: [http://autopackage.org/](http://autopackage.org/)

---

### Post by jdong on 2005-05-02
Debian/Ubuntu tries to do this with their .deb packages and the Synaptic GUI, but since every distro has its own blend of libraries and system layout, there's **no easy way to make a "universal" installer**. Most of them are centered around 'popular' distros, like RedHat/Fedora/SuSE.

Autopackage is an interesting initiative, but doesn't address the issue of conflicting library versions.


The LSB might help, if more application developers adhered to it.

---

### Post by j-rock on 2005-05-04
./configure && make && make install

seems universal enough to me.  But then again i could care less about the end user since most of them are still stuck trying to decide whether they should reboot or restart.  (not kidding, i've had to walk people through this multiple times at work)
](*,)  ](*,)  ](*,)

---

### Post by jdong on 2005-05-04
There are two ways of doing this:

1.) **Giving Fish to the Computers:**
Compile every single available piece of software available and package it specifically for the distro.

Debian/Ubuntu does this, and does a mighty fine job of it!

2.) **Teaching Computers how to Fish:**
Teach the computer how to compile software from source given a source package. Gentoo tries to do things this way. However, there are fewer packages in portage than in Debian :)




I'd like to see a hybrid -- a Portage+APT cross would solve most problems :)

---

