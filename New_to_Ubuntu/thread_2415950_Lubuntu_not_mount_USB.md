---
title: "Lubuntu not mount USB"
date: 2019-04-03
forum: New to Ubuntu
---

### Post by bunnyhop on 2019-04-03
Hi,
I'm new here.
Installed Lubuntu 18.10 32bits (Desktop DVD). Installed from HD with Grub4dos.
Very nice, what I was looking for.
At boot time if I leave a USB stick plugged in, the system stops loading (keeps displaying the Lubuntu logo). It continues loading if I take the USB stick out.

When the GUI is loaded, plugging in a USB, messagebox comes up to mount the USB drive and volumes, to view in the file manager. I click "Yes", the name of the drive appears in the file manager, but stops loading. If I pull out the stick the system freezes.

Tried different USB sticks. One HDD partition is NTFS, I will try to unmout it and try USB stick again. Or to mount via the shell.
I do not remember the USB mounting from LiveDVD GUI.

Toshiba Tecra A9 (2007). Not UEFI AFAIK.

Any help appreciated. Thanks


Plus, how do I recover my password for the forums. I'm logged in (autologin from phone) but I dont remember my pwd and can't change it!

---

### Post by yancek on 2019-04-03
You indicate that you have one ntfs partition on your drive but mention only one operating system (Lubuntu).  If that's the case,  no need for an ntfs partition.  If it's not the case, what other OS/version do you have?  What's on the usb and what type filesystem?

---

### Post by bunnyhop on 2019-04-03
Thanks.
WinRE on 1st (I kept on HD just for test purposes)
XPSP3 on 2.
Ubuntu on 3.

USB boots to Grub4dos, has mainly just mp3 on it. Fat16 and Fat 32 used on most of my USB sticks. Multipartition.

---

### Post by bunnyhop on 2019-04-03
Right.
I tried with a single partition 1GB USB stick. This time it appeared in PCMan and the files (jpgs) were displayed.
But when I clicked to open a jpg it took ages and didn't open it.

Also I had a space problem. Various times it has frozen and I used the power button to turn off. Then I ran into "no space left on the device" when I tried various shell operations and unmounts. I have read the /tmp folder might get clogged up if not shut down properly. I tried to delete /tmp files. Then using the navigation arrow in PCMan, at each click the "Free Space" indicated several GB less. 25GB total,  with install of 5 GB, but now I have only 6GB free.

We are talking / (root) folder, so what is happening?

---

### Post by yancek on 2019-04-03
> At boot time if I leave a USB stick plugged in, the system stops loading (keeps displaying the Lubuntu logo). It continues loading if I take the USB stick out.


What happens if you boot without the usb stick plugged in?

You have an xp install and Grub4dos.  That's a modified Grub designed to work on windows which I have never used so can't help with that.

> When the GUI is loaded, plugging in a USB, messagebox comes up to mount the USB drive and volumes, to view in the file manager. I click "Yes", the name of the drive appears in the file manager

Are you able to access it from the standard location, the /media or /media/username directory?  Generally listed by UUID.

> USB boots to Grub4dos, has mainly just mp3 on it. Fat16 and Fat 32 used on most of my USB sticks. Multipartition

Is this a bootable usb with some OS or utility on it?  You seem to indicate above that it is just data like images?

Don't remove the usb without first using the safely remove option.

---

### Post by bunnyhop on 2019-04-04
> **yancek said:**
> What happens if you boot without the usb stick plugged in?

Boots normally.

> **yancek said:**
> 
Are you able to access it from the standard location, the /media or /media/username directory?  Generally listed by UUID.

I can't access anything when the particular (partitioned) USB is plugged in. PCMan freezes really.

> **yancek said:**
> 
Is this a bootable usb with some OS or utility on it?  You seem to indicate above that it is just data like images?

Don't remove the usb without first using the safely remove option.

One USB (16GB) is bootable to Grub4dos, booting a liveos from a FAT32 partition. It also contains mp3s and has another FAT32 partition, also with mp3s. I might reformat / repartition (and try with 1 partition), to "clean" the partitioning.

A second USB (1GB) contains jpgs and is a single partition.

I remove the USB when PCMan is frozen for 5 minutes. Then the system freezes.

---

### Post by bunnyhop on 2019-04-05
Kind of related,
unmounting USB on Ubuntu 17.04 made the system freeze. Related to how filemanagers issue the commands.
Posting for reference, though my problem is different.


[https://www.linuxquestions.org/questions/linux-desktop-74/system-freeze-after-user-unmount-of-usb-device-with-thunar-4175643206/](https://www.linuxquestions.org/questions/linux-desktop-74/system-freeze-after-user-unmount-of-usb-device-with-thunar-4175643206/)

---

### Post by bunnyhop on 2019-04-06
Okay.

The low disk space problem was caused by the sizes of logs.

/var/log/kern.log
/var/log/syslog.1

Both 8GB each.
there might be other log files/temp files here and there on the system.

I first read about it with the /temp folder some people find full of files.
I did a
du -s ./* |sort

The problem (which fills the log files) is kernel ehci-pci dma_direct_map. It is a documented error.

---

