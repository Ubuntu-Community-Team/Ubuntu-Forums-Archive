---
title: "[SOLVED] resize /boot partition"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-06-03
New to Ubuntu.  Running Hardy on a dual boot machine.  Tried to use synaptics to install something and got the following:

Setting up linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-ubuntu-modules-2.6.24-17-generic
linux-image-generic
linux-generic

If I use system monitor, the size of the /boot partition is only 37.9 MiB, free space in /boot is just 3.1 MiB.  So I think I need to increase the size of the /boot partition.  It is in /dev/sdc11.

How does one change the size of a partition?

---

### Post by NikoC on 2008-06-03
Hmmz, I think you have a couple of options:

- boot from the Ubuntu livecd and start gparted partition editor (ALT + F2 > gksudo gparted)
- download the Gparted livecd [here]("http://gparted.sourceforge.net/livecd.php") and use it to boot from and resize

I think this should do the trick... though you might want to wait on some feedback from other forum members since I 've never tried this one before on an installed Ubuntu system...

---

### Post by cosine352 on 2008-06-03
look at this 

[http://ubuntuforums.org/showthread.php?t=134351]("http://ubuntuforums.org/showthread.php?t=134351")

---

### Post by ruffEdgz on 2008-06-03
I use gParted and it can be found by downloading it by

```

sudo apt-get install gparted

```

I sometimes use Parted Magic ([http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)) which is a nice live CD version for managing partitions and other things :D

Hope that helps.

---

### Post by indytim on 2008-06-03
RuffEdgz,

Unfortunately it won't be of much help here.  You can't do any active partition work on your booted partition.  That's why the other suggestor pointing to either booting to the LiveCD or else booting to the GParted Live CD are viable options for this situation.

IndyTim

---

### Post by ruffEdgz on 2008-06-03
Good point indytim

I didn't read that part carefully but it's good that my second option will work (using the PartedMagic Live CD) :D

---

### Post by raymondvillain on 2008-06-04
Parted Magic was the answer!  I had to "move 3 partitions to the right" and change their sizes so I could expand /dev/hd11.  It took about an hour but now I'm up and running, didn't lose anything.

Thanks for all the help.

---

