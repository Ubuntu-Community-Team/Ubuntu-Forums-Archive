---
title: "Irejuvenate an internal hdd using dd command"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by ityro on 2008-08-22
Is it safe to use the dd command   dd if=/dev/hda of=/dev/hda   to rejuvenate my internal HDD when one of the partitions is formatted ntfs and contains windows xp?  How about using the same command on an external removable HDD half nfts and half ext3? 

I thank you for your time . . .





My System:  Dual boot Ubuntu 8.04 (separate home folder) with XP on a HP COMPAQ   nx9010 Notebook,  Intel Pentium 4 CPU 2.66GHz,  706MB RAM,  40GB HDD,  USB 2.0,  CD-R Drive,  Floppy Drive,  80GB External HDD.  Single user for home use only.

---

### Post by srt4play on 2008-08-27
> **ityro said:**
> Is it safe to use the dd command   dd if=/dev/hda of=/dev/hda   to rejuvenate my internal HDD

What do you mean by rejuvenate? What are you trying to accomplish?

---

### Post by ityro on 2008-08-28
srt4play,  Thanks for your reply and sorry I did not respond sooner but I decided to trash my system and had to do a clean install which has not gone well, etc.
 
At this site: 
[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

I found the following:
Rejuvenate a hard drive
To cure input/output errors experienced when using dd. Over time the data on a drive, especially a drive that hasn't been used for a year or two, grows into larger magnetic flux points than were originally recorded. It becomes more difficult for the drive heads to decipher these magnetic flux points. This results in I/O errors. Sometimes sector 1 goes bad, resulting in a useless drive. 
I thank you for your time . . .

My System:  Dual boot Ubuntu 8.04 (separate home folder) with XP on a HP COMPAQ   nx9010 Notebook,  Intel Pentium 4 CPU 2.66GHz,  706MB RAM,  40GB HDD,  USB 2.0,  CD-R Drive,  Floppy Drive,  80GB External HDD.  Single user for home use only.

---

### Post by srt4play on 2008-08-29
Since dd just copies bit for bit, I don't think the filesystem type matters. Are you getting i/o errors or having some other type of data integrity problem that's making you want to do this?

---

### Post by ityro on 2008-08-29
srt4play, No problems with dd. Just trying to learn things that may be helpful later. Like I was doing when I trashed my system the other day. My clean install came with problems so I have learned some things to be more careful with. But no known problems with dd and I thank you for your time.

---

