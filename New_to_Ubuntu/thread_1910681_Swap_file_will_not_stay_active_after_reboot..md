---
title: "Swap file will not stay active after reboot."
date: 2012-01-17
forum: New to Ubuntu
---

### Post by TopHatMatt on 2012-01-17
So, I am currently attempting to add a swap file, not a swap partition as my laptop has already used up all 4 primary partitions for dual-booting purposes.

Currently I have managed to create a swap file, format, swapon and such, however after editing fstab and rebooting swap memory total returns with 0

In addition when trying to edit fstab using the line

```
gksudo gedit /etc/fstab
```I've been getting this in return before gedit opens the fstab file (have noticed that the number following (gksudo:XXXX) seems to vary)

```

(gksudo:2075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:2075): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```I have been using this guide for reference:
[https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

Any help regarding this issue will be greatly appreciated.

---

### Post by Double.J on 2012-01-17
Hi there! 

If you can sawpon and detect the swap space, then you've set it up right.. I'll just ask the obvious - no offence - where did you get the swap amount from? it wasn't showwing the amount of swap currently being used was it? just the amount of saw available?

Sorry had to ask, if it isn't mounting, best hava look at what you've got in your fstab.. would you mind posting the contents?

usually that warning means you need the GTK+ engine for pixbuf:
```

sudo apt-get install gtk2-engine-pixbuf

```

Hope it helps!

---

### Post by TopHatMatt on 2012-01-17
My swap file is the same as my ram/mem 2GiB.

fstab currently looks like this, all I did was add the file system to the end of it. (I have a Storage partition set up to share media between Win7 and Ubuntu)

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=615c3bb8-c96c-4732-bd1a-c04d0416988a /               ext4    errors=remount-ro 0       1
/media/Storage/2GiB.swap none   swap  sw       0  0



As for the GTK+ install, it returns this:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gtk2-engine-pixbuf

```

---

### Post by Double.J on 2012-01-17
Hi there 

First of all my bad, the package I was referring to should have been called
```

gtk2-engines-pixbuf
```
It was a long shot as it worked for me in 10.04.. but worth a try?

Next to the main problem! I think what's happened here is that you've set your swap on a seperate partition. This partition also isn't in the fstab, so it's not being mounted at boot; the system checks the fstab for mount options looks for the swap file, but as that device isn't set to mount can't access it without your permission once booted, so you have to manually swapon.

To be completely honest I'm not sure if fstab will be able to mount the swap file on another partition as it also has to mount that partition - try making an entry for that partition above your entry for the swap partition? it's a long shot again but may work, otherwise, the swap partition will have to be on your partition.

Hope it helps!

---

### Post by TopHatMatt on 2012-01-18
Sweet success! So, the installation of the gtk2-engines fixed that minor issue, and after adding the other partition to fstab and rebooting its mounting the swap file on start-up. Thank you for all the help. :D

---

