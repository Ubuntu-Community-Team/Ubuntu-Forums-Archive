---
title: "transfer files between ubuntu and puppy linux"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by golgo13 on 2008-06-12
and vice versa on pen drive
I am using a pen drive both as the boot and harddrive for an old desk top, without its own harddrive, to run puppy linux
I need to transfer files between this computer and my laptop running ubuntu 
the memory stick contains both the puppy linux distro and my 
pup_save-richard.2fs partition
I would like to access this partition in ubuntu but I cannot open it
which application would allow me to do this so I can edit files in ubuntu?
any help appreciated

---

### Post by kesman on 2008-06-12
When you insert the usb-stick into your ubuntu box, what happens? Install gparted and open it to view your partitions, and select the pen drive as the device.

---

### Post by marufaberlin on 2008-06-12
mount shouold do it as well.

---

### Post by golgo13 on 2008-06-12
its already mounted
my problem is that ubuntu cannot open the part of the pendrive that contains the puppy linux files
it views it as a program rather than files

---

### Post by kesman on 2008-06-12
So the partition is marked as a file? You mount it as as you would mount a cd-rom image.
First create a mount point. In my example it will be in your home dir:
```

mkdir ~/mountpoint

```
then mount the pup_save-richard.2fs into it:
```

sudo mount -o loop /path/to/pup_save-richard.2fs ~/mountpoint

```
and now you should be able to go to ~/mountpoint and see all your puppy files in it.

---

