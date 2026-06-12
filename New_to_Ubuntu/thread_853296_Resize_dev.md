---
title: "Resize /dev"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by skylar.sutton on 2008-07-08
Sorry for the rookie question...

How do you resize the /dev space allocation. I need to load some files into a folder under /dev that will be larger than 1GB but the discus output shows I am capped at 0.99GB:

```
Mount           Total         Used         Free       Prcnt      Graph
/               50.23 GB      2.74 GB     44.95 GB     5.5%   [*---------]
/sys                0 KB         0 KB         0 KB     0.0%   [----------]
/var/run         0.99 GB       100 KB      0.99 GB     0.0%   [----------]
/var/lock        0.99 GB         0 KB      0.99 GB     0.0%   [----------]
/dev             0.99 GB        52 KB      0.99 GB     0.0%   [----------]
/dev/shm         0.99 GB        12 KB      0.99 GB     0.0%   [----------]
+c/volatile      0.99 GB      37.8 MB     971.8 MB     3.7%   [----------]
+l/security         0 KB         0 KB         0 KB     0.0%   [----------]
+tton/.gvfs     50.23 GB      2.74 GB     44.95 GB     5.5%   [*---------]
```If I use gparted /dev/sda2 is an extended partition of 52Gb with two partitions under it /dev/sda5 is ext3 @ 50GB and /dev/sda6 is linux-swap @2 GB.

Basically I want to move some space allocated from / to /dev... thanks in advance!

---

### Post by jamesapnic on 2008-07-08
You should put files into /dev, its a file system used to access drivers.  In Ubuntu and most modern distros the files are created dynamically by the kernel.  What exactly are you trying to do?  i.e. why do you want to put files there?

---

### Post by decoherence on 2008-07-08
> **skylar.sutton said:**
> 
Basically I want to move some space allocated from / to /dev... thanks in advance!

/dev is a subset of / -- you don't allocate storage between them -- whatever is available to / is available to /dev. You can ignore what discus says about /dev because it's not a real partition but a dynamically generated directory that is as big as it needs to be.

Why do you ask?

---

### Post by chrisccoulson on 2008-07-08
As already pointed out, /dev/ is a tmpfs, so it doesn't really exist on any physical disk, and the contents of /dev are lost when you reboot the machine.

/dev is recreated dynamically by UDEV, and contains device nodes for hardware devices. You cannot use it for general storage, and trying to do so is likely to be a fast way to crash your machine

---

