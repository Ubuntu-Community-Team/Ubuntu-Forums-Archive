---
title: "ndiswrapper-utils help"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by misterhan on 2008-09-18
Hey I'm tring to use this guide
[http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)

but am not sure how to work ndiswrapper-utils

It says I don't have it, so how would I got about this?
Thank.

---

### Post by Jazzy_Jeff on 2008-09-18
Just go into Synaptic Package Manager and search for ndiswrapper. It should come up in the list and install it.

---

### Post by misterhan on 2008-09-18
I went there and all I have is one called ndiswrapper-common.

This is the command I'm trying to give.
sudo apt-get install ndiswrapper-utils

Not when I type that command in it gives me
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
han@han-laptop:~$ sudo apt-get install ndiswrapper-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ndiswrapper-utils is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  ndiswrapper-common
E: Package ndiswrapper-utils has no installation candidate

---

### Post by Sealbhach on 2008-09-18
Have you got Synaptic Package Manager open?

The package manager is already being used, is what that means.

.

---

### Post by misterhan on 2008-09-18
Nope nothing is open, only Terminal.

---

### Post by Sealbhach on 2008-09-18
I've just looked in Synaptic.

ndiswrapper-common

replaces

diswrapper-utils

so just install ndiswrapper-common


.

---

