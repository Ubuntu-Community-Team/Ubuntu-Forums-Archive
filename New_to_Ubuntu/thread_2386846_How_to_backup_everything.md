---
title: "How to backup everything?"
date: 2018-03-11
forum: New to Ubuntu
---

### Post by xipho2 on 2018-03-11
[I]Hi, 
[/I]
If the OS or the machine is broken, I want to pick up the external HDD, plug it into the USB socket and continue after restoring it, where I have left off. Everything does mean, e. g.:
All files and folders, preferences, options, installed software, changings. Thus having the machine, say, after an hour up and running. Some Linux OS's are shipped with a backup software, as in Mint. Are they doing what I want? If not, what should I do?

---

### Post by ajgreeny on 2018-03-11
Sounds as if you want and need a clone of your complete hard disk.
Have a look at clonezilla which is the only one I know, though there are other cloning applications and utilities.

[https://help.ubuntu.com/community/mkusb/persistent/clonezilla](https://help.ubuntu.com/community/mkusb/persistent/clonezilla)

---

### Post by TheFu on 2018-03-11
Everyone is different.  We all have different skills and different needs.  Different backup techniques are possible which drastically impact storage, security, versioning, ease of restore, ease of backups, and many other aspects. 

Only you can choose the best technique for your needs.

If you can prioritize the most important aspects for yourself, then you can drill down towards the best solution for YOUR needs.

Things like:
* bonehead restores
* versioned backups
* zero downtime backups vs 5 hrs of downtime
* leverage advanced file systems or not
* minimize storage use
* remote storage or local-only storage
* efficient network/offsite data transfers
* encryption used for storage
* leverage external services or not
* tied to a Unix file system or not

All popular Linux systems have multiple backup softwares trivially included through their package manager. sudo apt install {some-great-backup/restore-software} - that's all it requires.  dd is the most basic backup tool and it is included in 99.9999% of all Unix/Linux installs.

Regardless for which aspects you deem most important, nothing will replace testing the restore.  Nothing.  It took me about 5 backup attempts before I'd gotten a system that captured what I needed, but nothing more.  Reducing storage needs for the backups was VERY important to me and having daily, versioned, backups for 60-120 days was absolutely critical.  Also, minimizing downtime was important to me.

For most end-users, something like **aptik** is probably what they want for backups.  I use different types of backups for different needs on different systems.  Server backups are very different from desktop backups.  I have 2 desktops, but 25+ servers - so using a server backup method means I don't have to deal with different solutions and it always works.

If you look in these forums for "restore" and ( "fail" or "corrupted") you can see which backup systems fail to restore from time to time.  After all, we spend most of our time doing backups when a backup that doesn't actually work for a restore is completely a waste of time.  Backups are 10%. It is the restore that is 90% - the entire reason we bother. TEST the restore.  Please.

Oh ... a few tools for your consideration:
* dd / ddrescue (bit-for-bit; no versioning)
* fsarchiver (file system + compression; no versioning)
* partimage / clonezilla  (imaging + compression; no versioning)
* duplicity / deja dup / duplicati (duplicity-based- local/network, encrypted, old-school style)
* rsnapshot / rbackup / sbackup / back-in-time (these are all rsync + hardlink; tied to Unix file system)
* rdiff-backup (rdiff/rsync network backup w/ efficient versioning; efficient storage)
* aptik (lets users choose what to be backed up; may not support versioning)

I've used most of them for a month or so over the decades.  rdiff-backup is what I use today and have been using since around 2010.  I use advanced file system techniques to end any downtime thanks to LVM2.  Most people new to Linux/Unix aren't ready for the extra effort needed to setup and use LVM.  LVM makes image-based backups a little harder, but file-system based backups are drastically aided by using an LVM snapshot technique.

If you just want to know "what button do I press" - look at aptik first. If that doesn't do what you want, clonezilla is very popular if you want bit-for-bit **everything** backups. Clonezilla has to be run from alternate boot media. Most imager backups require that so the backups don't get corrupted.

---

### Post by sudodus on 2018-03-11
> **ajgreeny said:**
> Sounds as if you want and need a clone of your complete hard disk.
Have a look at clonezilla which is the only one I know, though there are other cloning applications and utilities.

[https://help.ubuntu.com/community/mkusb/persistent/clonezilla](https://help.ubuntu.com/community/mkusb/persistent/clonezilla)

+1

Normally I use [Clonezilla](http://clonezilla.org) from a 'stable' iso file and am happy with it. Boot Clonezilla from a CD/DVD disk or USB pendrive.

You have two options, when you run Clonezilla:

1. Create a cloned copy in a drive of at least the same size as the original one. It can be used at once (after replacing the original drive).

2. Create a compressed image in anoither drive. A Clonezilla image is a directory with a number of files. This will usually be much smaller than the size of the original drive (because of the compression, but also because Clonezilla is smart enough to only clone used blocks on the drive). You can have more than one such Clonezilla images.

Whichever way you choose, you should test, that the cloned copy or the compressed image is good. The compressed image should be restored to a [new] drive of at least the same size as the original one. This test is important, otherwise you cannot really rely on your backup method.

[hr][/hr]
The backup method with Clonezilla is slow and cumbersome, but complete.

It is a good idea to have another backup method too, with some backup too&#314;, that backs up the files, that you cannot afford to lose, typically the personal files. This backup is usually much faster, and it can be done manually when you have created important files, and automatically for example every night.

[help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by sudodus on 2018-03-11
> **TheFu said:**
> Everyone is different.  We all have different skills and different needs.  Different backup techniques are possible which drastically impact storage, security, versioning, ease of restore, ease of backups, and many other aspects. 

Only you can choose the best technique for your needs.

If you can prioritize the most important aspects for yourself, then you can drill down towards the best solution for YOUR needs.

Things like:
* bonehead restores
* versioned backups
* zero downtime backups vs 5 hrs of downtime
* leverage advanced file systems or not
* minimize storage use
* remote storage or local-only storage
* efficient network/offsite data transfers
* encryption used for storage
* leverage external services or not
* tied to a Unix file system or not

All popular Linux systems have multiple backup softwares trivially included through their package manager. sudo apt install {some-great-backup/restore-software} - that's all it requires.  dd is the most basic backup tool and it is included in 99.9999% of all Unix/Linux installs.

Regardless for which aspects you deem most important, nothing will replace testing the restore.  Nothing.  It took me about 5 backup attempts before I'd gotten a system that captured what I needed, but nothing more.  Reducing storage needs for the backups was VERY important to me and having daily, versioned, backups for 60-120 days was absolutely critical.  Also, minimizing downtime was important to me.

For most end-users, something like **aptik** is probably what they want for backups.  I use different types of backups for different needs on different systems.  Server backups are very different from desktop backups.  I have 2 desktops, but 25+ servers - so using a server backup method means I don't have to deal with different solutions and it always works.

If you look in these forums for "restore" and ( "fail" or "corrupted") you can see which backup systems fail to restore from time to time.  After all, we spend most of our time doing backups when a backup that doesn't actually work for a restore is completely a waste of time.  Backups are 10%. It is the restore that is 90% - the entire reason we bother. TEST the restore.  Please.

Oh ... a few tools for your consideration:
* dd / ddrescue
* fsarchiver
* partimage / clonezilla
* duplicity / deja dup / duplicati
* rsnapshot / rbackup / sbackup
* rdiff-backup
* aptik

I've used most of them for a month or so over the decades.  rdiff-backup is what I use today and have been using since around 2010.  I use advanced file system techniques to end any downtime thanks to LVM2.  Most people new to Linux/Unix aren't ready for the extra effort needed to setup and use LVM.

If you just want to know "what button do I press" - look at aptik first. If that doesn't do what you want, clonezilla is very popular if you want bit-for-bit **everything** backups. Clonezilla has to be run from alternate boot media. Most imager backups require that so the backups don't get corrupted.

+1

This is great advice :-)

---

### Post by wrongusername2 on 2018-03-11
I have two physical disks. One is *OS disk* and other is *data-disk*. I have created clone of *OS disk* only using CloneZilla. I do not clone the *data disk*. Whenever there is a machine problem I restore the image on to *OS disk*. Restore operation will not touch the *data-disk. *I suggest, store the *data* and *os *on different disks*. *You can also store the *data* on an external hard drive. So when you restore the* OS disk*, it will not overwrite your data.   Watch youtube videos to know how to run clone-zilla.  I suggest that you practice backup and restore at least once.

---

### Post by kevdog on 2018-03-11
Clonezilla works, however its a really cumbersome process.  Hard to keep a bunch of backup disk copies for me laying around.  Others may be better at it for me.

I've looked at backup solutions for a while -- and there doesn't exist a perfect solution. I usually just need the data backed up -- not the OS or boot partition (although I do back up /etc since this has the various configurations I use).  I've been using a program called borg for a while.  [https://borgbackup.readthedocs.io/en/stable/quickstart.html](https://borgbackup.readthedocs.io/en/stable/quickstart.html).  It works for me since I wanted a versioned backup and I wanted to encrypt the backup copy as well, and I only wanted to backup diffs of changes (after the first backup is made of course), rather than copying every single file over with everybackup.  Its very similar to rsnapshot and rdiff-backup however it adds encryption -- I'm not sure if this is important for you.   I believe clonezilla only backs up to media.

---

### Post by monkeybrain20122 on 2018-03-12
fsarchiver, it is in the repo. [http://www.fsarchiver.org/](http://www.fsarchiver.org/) More flexible than Clozilla and can clone clone your partition when you are using the computer.

---

### Post by oldrocker99 on 2018-03-12
Make sure that you are copying the /home folder, where all your downloads and program settings are kept.

I personally use grsync, which does the job for me, except that the progress window shows 99% long before the project ends.

---

### Post by mastablasta on 2018-03-12
if only OS is broken but hardware is good (e.g. disk is ok), then you could use an advanced file system (such as ZFS4linux or BTRFS) to restore the OS to previous state via snapshots.

---

### Post by TheFu on 2018-03-12
> **mastablasta said:**
> if only OS is broken but hardware is good (e.g. disk is ok), then you could use an advanced file system (such as ZFS4linux or BTRFS) to restore the OS to previous state via snapshots.

Or LVM snapshots.

---

