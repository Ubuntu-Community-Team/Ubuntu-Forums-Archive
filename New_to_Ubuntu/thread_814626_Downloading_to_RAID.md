---
title: "Downloading to RAID"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by keval on 2008-05-31
I've just installed two 500 gig internal HDs as RAID1 for use as a media server.  I'm booting off a 150 gig HD.  How do I route downloads to the RAID disks and not to the boot disk?  I need to make the process automatic so my kids' music downloads will go directly to the RAIDs and not the boot disk.
Thanks,
Kevin

---

### Post by quelx on 2008-05-31
Well...  You could use a symlink or reconfigure the app doing the downloading. Where is you app currently storing downloads and where is your new array mounted?

---

### Post by tamoneya on 2008-05-31
just put the raid in fstab and mount it to something like /storage. Then tell the program to download all of the music and stuff to /storage.  The method for doing this depends entirely on what you are using to do the downloading.  If you give us more details on this we could help you out with getting this setup.

---

### Post by keval on 2008-05-31
What kind of info do you need?  I have the two RAID disks running off a control card.  When I run fdisk -l, the system can see the disks, but when I do cat /proc/mdstat it shows nothing.  when I download, I see no option for sending the data to the RAID.
Anyway, let me know what info would be helpful and I'll provide it.
Thanks,
Kevin

---

### Post by quelx on 2008-05-31
So you haven't created the array?

if not
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

the array must be **created**/**formated**/**mounted** before you can write data to it, the above will get you through those steps.

---

### Post by keval on 2008-06-01
Greetings.
I've already created the array, but probably have not mounted it correctly.
Following is my fdisk -l output:

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14335   115145856   fd  Linux raid autodetect
/dev/hda2           14336       14593     2072385    5  Extended
/dev/hda5           14336       14593     2072353+  82  Linux swap / Solaris

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d0e4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          61      489951   fd  Linux raid autodetect
/dev/sda2              62         304     1951897+  fd  Linux raid autodetect
/dev/sda3             305       60801   485942152+  fd  Linux raid autodetect

As I think this indicates, my machine can detect the RAID1 (read as a single 500 GB HD).

---

