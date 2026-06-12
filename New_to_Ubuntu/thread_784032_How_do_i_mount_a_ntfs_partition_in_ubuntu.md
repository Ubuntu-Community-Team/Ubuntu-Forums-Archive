---
title: "How do i mount a ntfs partition in ubuntu?"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by monkspeed on 2008-05-06
Hello all, my XP installation just died so i wiped it and installed Ubuntu. I have a separate NTFS partition with my "My Documents" data on, but it is not showing in Ubuntu. How do i get it to appear?

I'm a total Ubuntu/Linux noob.

Any help gratefully received, thanks.

---

### Post by kpkeerthi on 2008-05-06
Does it show up when you run this command in a terminal?
```
sudo fdisk -l
```

---

### Post by omns on 2008-05-06
Install ntfs-config with Synaptic Package Manager and then use its GUI control panel to add the drive. It will install into

Applications-->System Tools-->NTFS Configration Tools

---

### Post by monkspeed on 2008-05-06
thanks for the super quick reply!

i get this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d3cb334

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2   *        5152        9729    36772785    7  HPFS/NTFS
/dev/sda3            1217        1459     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

i see the only ntfs partition is marked as boot but it wasnt the boot drive, only a data partition.

---

### Post by bumanie on 2008-05-06
Install ntfs-3g and ntfs config via synaptic and then go to Applications --> System Tools --> Ntfs configuration tool and you will be able to give yourself read/write privileges to the ntfs partition.

---

### Post by kpkeerthi on 2008-05-06
> **monkspeed said:**
> thanks for the super quick reply!

i get this

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6d3cb334

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2   *        5152        9729    36772785    7  HPFS/NTFS
/dev/sda3            1217        1459     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

i see the only ntfs partition is marked as boot but it wasnt the boot drive, only a data partition.

Follow [this]("http://ubuntuforums.org/showpost.php?p=4757851&postcount=6") guide step-by-step.

---

### Post by monkspeed on 2008-05-06
Ok this is what i get for both methods...

$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2 ntfs-3g defaults,force 0 0
ntfs-3g: Cannot mount 'dev/sda2': No such file or directory

ntfs-3g 1.913 - Third Generation NTFS Driver

Copyright (C) 2005-2006 Yura Pakhuchiy
Copyright (C) 2006-2007 Szabolcs Szakacsits

Usage:    ntfs-3g <device|image_file> <mount_point> [-o option[,...]]

Options:  ro, force, locale=, uid=, gid=, umask=, fmask=, dmask=,
          streams_interface=. Please see details in the manual.

Example:  ntfs-3g /dev/sda1 /mnt/win -o force,locale=en_EN.UTF-8

Ntfs-3g news, support and information:  [http://ntfs-3g.org](http://ntfs-3g.org)

cheers

---

### Post by kpkeerthi on 2008-05-06
Both method? What command did you type? And perhaps, you may want to do as it suggests
> 
Choice 1: If you have Windows then disconnect the external devices by
clicking on the 'Safely Remove Hardware' icon in the Windows
taskbar then shutdown Windows cleanly.

If it is not an external drive, simple boot into windows and make sure you shut it down cleanly. And then try the link I posted.

---

### Post by bodhi.zazen on 2008-05-06
Try this :

```
sudo mount -t ntfs-3g /dev/sda2 /media/sda2 -o force
```You get that error message if for some reason the partition / device was uncleanly unmounted. Typically you can boot windows and re-mount the partition for maintenance.

Since you are no longer running windows I suggest you move the data off the ntfs partition, re-format it to ext3, and then restore the data.

---

### Post by bumanie on 2008-05-06
If the above doesn't work post the output of > cat /etc/fstab

---

### Post by monkspeed on 2008-05-07
> **kpkeerthi said:**
> Both method? What command did you type? And perhaps, you may want to do as it suggests

If it is not an external drive, simple boot into windows and make sure you shut it down cleanly. And then try the link I posted.

windows is long gone!

> **bodhi.zazen said:**
> Try this :

```
sudo mount -t ntfs-3g /dev/sda2 /media/sda2 -o force
```You get that error message if for some reason the partition / device was uncleanly unmounted. Typically you can boot windows and re-mount the partition for maintenance.

Since you are no longer running windows I suggest you move the data off the ntfs partition, re-format it to ext3, and then restore the data.

i cant move data off the drive because the drive does not show up!

> **bumanie said:**
> If the above doesn't work post the output of

Hi i will do as soon as i can, i have left the laptop at my parents as i had to rush away on an emergency. I will do as you say asap and let you know.

Thanks for the quick replys!

---

### Post by bodhi.zazen on 2008-05-07
> **monkspeed said:**
> 

i cant move data off the drive because the drive does not show up!

Can yo be more specific ? does the partition mount with the force option or did you get another error ?

If no error, what happens when you :

```
ls -la /media/sda2
```

or

```
gksu nautilus /media/sda2
```

---

### Post by monkspeed on 2008-05-19
Hello all, this is the first time in a few weeks i've been able to try your tips, i would like to say thanks to all for your comments.

kpkeerthi > Thanks a million matey, all your instructions were right on the button. :guitar: Although i havent got the drive on the desktop, i can access it through media/windows

---

### Post by Joeb454 on 2008-05-19
Hi, please try out the link in my sig (the one at the bottom) and see if that works for you :)

---

