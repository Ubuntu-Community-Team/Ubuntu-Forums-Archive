---
title: "One of my partitions does not show up in Ubuntu"
date: 2014-04-19
forum: New to Ubuntu
---

### Post by NA3OH on 2014-04-19
I dual boot with Win7 and I'm able to access all partitions except for my media partition which is ~300GB and formatted as NTFS. I have no idea why I cant access it, considering I can access all of my other NTFS partitions. 

The partition doesnt show up at al is what I mean. I cant get to it through the file manager.

---

### Post by david98 on 2014-04-19
Can you see the partition when you type this command in the terminal  sudo fdisk -l  ?

---

### Post by NA3OH on 2014-04-19
Going to be perfectly honest, I cant really tell from the info. Here's the data. MY HDD is set up like this.

~320GB partition for Media (books, movies, tv shows)
~100GB for Windows 7
~30GB for Ubuntu
~20GB for Linux Mint (just trying it out)
~100GB partition for Video Games
~10GB partition for personal data


```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          208845   209937419   104864287+   7  HPFS/NTFS/exFAT
Partition 2 does not start on physical sector boundary.
/dev/sda3       209940478  1250262976   520161249+   f  W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5       209940480   388198399    89128960    7  HPFS/NTFS/exFAT
/dev/sda6       388210788   451123299    31456256    7  HPFS/NTFS/exFAT
Partition 6 does not start on physical sector boundary.
/dev/sda7       451201653  1153823645   351310996+   7  HPFS/NTFS/exFAT
Partition 7 does not start on physical sector boundary.
/dev/sda8      1174725386  1227151167    26212891   83  Linux
Partition 8 does not start on physical sector boundary.
/dev/sda9      1227151360  1250262976    11555808+   7  HPFS/NTFS/exFAT


```

---

### Post by oldfred on 2014-04-20
It looks like sda7 as that is about the correct size.

When you say you cannot see it, is it just in Ubuntu but works ok in Windows or not in both?

Have you tried chkdsk from Windows on that partition? Ubuntu will not mount hibernated systems or partitions needing chkdsk.

When you start having more partitions I like to label them so then I know what they are. Then the Nautilus file manager will mount with labels if not auto mounted with fstab.

I try to remember to label when I create partitions with gparted, but often forget or need to change a label and then use disks or disk utility (depending on version of Ubuntu).

An older screen shot showing labels in left panel and disk utility where the edit partition has a label change.

---

### Post by NA3OH on 2014-04-20
I can see and access it when I'm using Windows.

Will try to figure out how to do the other suggestions you listed. Really hope I can fix this as I spend a decent amount of time using that partition

---

### Post by NA3OH on 2014-04-22
For some reason when I run chkdsk in windows, it just opens cmd for a split second and closes. I'll try it again tomorrow though. Not really sure why this is, but it doesn't look like I can use it at the moment.
The partition in question is sda7 by the way

As a pretty big noob at Linux, pretty much have just started using it, can you dumb the instructions down a bit?
What is a hibernated system and why is this partition one? I didn't do anything differently from when I created my other partitions. How do I not make it a hibernated partition?
"Then the Nautilus file manager will mount with labels if not auto mounted with fstab." How do I set this up? I already have them all labelled.


I'll post a pic of my partition layout tomorrow as gparted won't run right now (installing 14.4 so maybe that's why).

---

### Post by oldfred on 2014-04-22
The NTFS driver with Linux does not normally let you mount partitions that have chkdsk flag or hibernation flag to try to prevent damage to the partition that forcing data into may further corrupt system. But new Windows 8 have a partial hibernation called fast boot that causes issues. Not sure that in Windows there is a way to unmount a partition.

---

### Post by NA3OH on 2014-05-11
Ended up just merging 2 partitions and the problem is solved now.

---

