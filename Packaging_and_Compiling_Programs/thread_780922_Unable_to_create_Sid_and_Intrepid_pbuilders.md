---
title: "Unable to create Sid and Intrepid pbuilders"
date: 2008-05-03
forum: Packaging and Compiling Programs
---

### Post by andrewsomething on 2008-05-03
I'm trying to use the pbuilder-dist script to create pbuilders for multiple distributions. Both Debian Sid and Ubuntu Intrepid are failing.

```
...

I: Installing core packages...
W: Failure trying to run: chroot /var/cache/pbuilder/build/22927/. dpkg --force-depends --install var/cache/apt/archives/libc6_2.7-10_i386.deb
pbuilder: debootstrap failed
 -> Aborting with an error
 -> cleaning the build env 
    -> removing directory /var/cache/pbuilder/build//22927 and its subdirectories
```


Any ideas?

---

### Post by pro003 on 2008-05-07
i have tried to install hardy to my friends desktop today and i got this message inn the middle of installation DEBOOTSTRAP ERROR with some path leading to this :

```
dpkg --force-depends --install var/cache/apt/archives/libc6_2.7-10_i386.deb
```


I was unable to continue installation.

have no idea what the heck is this error...:confused:

---

### Post by andrewsomething on 2008-05-07
Apparently it has to do with these bugs:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=479202](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=479202)

[https://bugs.edge.launchpad.net/debian/+source/perl/+bug/227560](https://bugs.edge.launchpad.net/debian/+source/perl/+bug/227560)

---

