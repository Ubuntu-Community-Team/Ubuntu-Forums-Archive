---
title: "[SOLVED] help with external hd"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by kingpin393 on 2008-10-19
Hi,

I have an external hd that has tons of stuff on it that I used with Vista.  I recently installed Ubuntu on a partition.  I put some stuff on it with Ubuntu and now when I try and open it in windows again it say I need to format it to use it.

What happened here?  Is there any way I can fix this?

Thanks,
Kevin

---

### Post by BDNiner on 2008-10-19
Are you able to view the drive when you are booted into ubuntu? I would install gparted in ubuntu so that i can see the drive's partition layout.

---

### Post by kingpin393 on 2008-10-19
yes I can see the drive and manipulate it in ubuntu still

---

### Post by kingpin393 on 2008-10-19
I installed gparted - what should I be looking at here?

the drive has an NTFS filesystem with a mount point of /media/STORAGE_2

---

### Post by BDNiner on 2008-10-19
OK, does the NTFS file system take the whole drive or are there other partitions present on the drive? I would copy all the data off the drive in ubuntu and then format it to the NTFS file system and copy the data back and then try and see if it works in Vista.

---

### Post by bpowell2005 on 2008-10-19
> **kingpin393 said:**
> Hi,

I have an external hd that has tons of stuff on it that I used with Vista.  I recently installed Ubuntu on a partition.  I put some stuff on it with Ubuntu and now when I try and open it in windows again it say I need to format it to use it.

What happened here?  Is there any way I can fix this?

Thanks,
Kevin

Another thing to check is to make sure you're unmounting the external drive before you unplug it...failure to unmount could result in the NTFS file system becoming corrupt...although, Windows doesn't seem to mind this as much, it's just an idea of something to look out for.

---

### Post by kingpin393 on 2008-10-19
I tried unmounting before i unplugged it but windows still asks me to format.

The problem with copying it to the ubuntu partition and formatting the drive is I don't have enough space to do that...

But even if I repartitioned the computer to give me enough space how will that be different than what got me into this mess...  I copied files to the drive to begin with...

I did delete some files on it as well... would that have caused an issue?  I still want to know why this happened.  I know it has to do with ubuntu because i was using the drive on vista earlier today.

Kevin

---

### Post by kingpin393 on 2008-10-20
Ok so I am reformatting to give my ubuntu partition enough space for me to copy all the files from the external HD over.  

Once I copy the files over what is my next step?  How do I get it so windows can read it again?

Thanks,
Kevin

---

### Post by BDNiner on 2008-10-20
Go ahead and format it in windows. Before you boot back into ubuntu you should eject the disk from my computer.

---

### Post by kingpin393 on 2008-10-20
ok done, I unplugged it before I rebooted into Ubunutu...

Should I plug it back in now?

---

### Post by BDNiner on 2008-10-21
yes plug it back into ubuntu, copy the files back, then make sure to eject it before you boot back into windows. Windows should now correctly read the drive. If you have issues reading the drive now then there maybe a physical problem with your harddisk.

---

### Post by kingpin393 on 2008-10-21
Looks like it all worked out.

Thanks for the help guys.

-Kevin

---

