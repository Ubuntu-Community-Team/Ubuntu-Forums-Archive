---
title: "HDD on the way out, any way to image install?"
date: 2013-03-25
forum: New to Ubuntu
---

### Post by chadwell on 2013-03-25
I have a laptop which I use as a NAS.  The internal HDD is dying and I'm getting a lot read errors.  I am going to buy a new harddrive, partition it and put ubuntu on it.  But I'm wondering if there is a simple way I can reinstall my version of ubuntu, with all the programs and settings etc.

It would save me a whole lot of hassle.

Be even better if I could do all this via usb stick.

Any ideas?

---

### Post by Redalien0304 on 2013-03-25
Clonezilla or Redobackup

---

### Post by chadwell on 2013-03-25
Thanks - seems you need a cd for those, any way to use USB? <edit> - sorry looks like you can use USB after all

---

### Post by chadwell on 2013-03-25
On my current setup I have a 1TB drive, this is partitioned to have 15GB for the O/S, and the rest is for files (music, video etc).  The large partition is under sda3/media/NAS.
Anyway to *only* image the smaller partition - where all the O/S info should be?

---

### Post by oldfred on 2013-03-25
While many like and use Clonezilla, I suggest the clean install. It then automatically housecleans and avoids issues of duplicate UUIDs in grub & fstab. If not keeping old drive the duplicate UUID is not as large of an issue.

With a clean install you do want to have /home and a list of installed applications. But that should be part of your normal backup.
       Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
backup the following:

   1. /home (Users' personal files and settings) including keys in ~/.gnupg
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup
5. list of installed applications 

Also if a server do you have any other applications that save data into / like a database? Then you also need to back up those folders. And you may have custom settings in /etc but do not reinstall as new system may not need them or they may conflict if a new install.

---

### Post by chadwell on 2013-03-25
Thanks for the reply.Just saw it after having used clonezilla to make a "saved parts" backup.

I Backed up my sda2 partition to a usb stick.


if I get a new hdd, and partition it and put ubuntu on sda2, can I just restore my backup to the new sda2? 


 Does it have to be the same size, and same format I.e. ext3.Could I use ext4 instead? 
Will all my apps and data be restored? 


Thanks!

---

### Post by chadwell on 2013-03-26
Just looking clarification of above.  If I put in a brand new HDD, do I need to reinstall Ubuntu completely - or is it sufficient to restore my "saved parts" clonezilla backup to the fresh HDD.  Which is my SDA2 partition.  I did not save my SDA3 partition as this is the NAS part of my HDD which contains all music, movies etc.

---

