---
title: "Needed features (?)"
date: 2009-07-06
forum: Recurring Discussions
---

### Post by crobruncato on 2009-07-06
I've been using ubuntu for a while now (off and on since early versions). It's now my main laptop OS, and has been for a year or so. Having said that...

I think ubuntu should focus on only a few things for one of the next builds.
One issue I would recommend work on is basic sound. It works pretty well on my laptop but I've seen and had issues with getting sound to work. The other big issue, and probably the biggest IMO, is backup. I would like to see an easy yet complete backup of the entire system with an easy restore method. 

From the windows world, think either Acronis or Windows Home server. Ideally, I'd have a backup of my drive to an external hard drive (or file server), and, if my drive went, I'd be able to boot off an Ubuntu install CD and restore completely from a backup. Both the backup and restore should be simple, not command line driven. The backup should be a scheduled event as well.

I see a fair number of computers where I work, and a lack of backups. Windows is starting to make imaged based backups easier  - in the case of WHS, much easier. I suggest that Ubuntu can do it as well. 

If there is a way to make this an official "suggestion" or request to the developers, could someone point me to the proper location. If this has already been suggested- I'd second the motion.

Thanks, and I'm awaiting the flames or suggestions.:p
Rob

---

### Post by Temposs on 2009-07-06
The best way to make suggestions like this is to use [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

You can see what other people want Ubuntu to be working on as well, and comment and vote on ideas. It's a great site, and the ubuntu developers do look at the most popular ideas, at least.

As for sound, I think Ubuntu's use of pulseaudio has set back the sound functionality in Ubuntu somewhat, despite the claimed benefits. I don't think they're removing pulseaudio in the next version, though.

In terms of backup, I've been using a program called Deja Dup. It's in the Add/Remove repositories, and it's very simple to use. It's also actively being developed, which is something to look for in the software you use. Something cool about Deja Dup which sets it apart is that it has built-in support for backing up to Amazon S3:
[http://mterry.name/deja-dup/](http://mterry.name/deja-dup/)

If you want a more complex backup solution, you might look at Bacula, which I haven't tried, but seems very robust and actively developed. It's also in the Ubuntu Add/Remove repositories: [http://www.bacula.org/en/](http://www.bacula.org/en/)

If you like the Rackspace/Amazon S3 "cloud" backup infrastructure, and you don't mind paying for backup services, the program called Jungle Disk looks quite nice, and I may start using it for the company I work for. It's nice for individual use too, though. It's completely cross-platform, so you can use it between any of your Windows, OSX, and Linux computers:  [http://www.jungledisk.com](http://www.jungledisk.com)

You might also check out Ubuntu One, which is just getting started as a file syncing and backup service from Canonical(the company that makes Ubuntu), and is a possible solution for backup: [https://ubuntuone.com/](https://ubuntuone.com/)

Another service similar to Ubuntu One is Dropbox, which is a cross-platform file syncing and backup service that's also still getting started but they are further along: [http://www.getdropbox.com/](http://www.getdropbox.com/)

---

### Post by carml on 2009-07-06
Have you asked somewhere on the forum? Maybe some suggestion can solve your issue with backup.
Also if you think there's some missing feature get a look here[HTML]http://brainstorm.ubuntu.com/[/HTML] and check if there's already something similar to your idea/s or if you want something to be implemented just add your suggestion there. :)

---

### Post by Cope57 on 2009-07-06
A separate partition for /home has always done well as my backup.
A simple create archive of /home like cope57.tar.gz and move it to another PC or uploaded to a webserver has always been my best backup.

Other ways to backup could be applications like afbackup, amanda-client, backup2l, backup-manager, backupninja, backuppc, bacula, cedar-backup2, chiark-backup, dar, dirvish, faubackup, hdup, keep, and so on...

There are numerous ways to backup a system or files, you need to decide which works best for you. I only need a backup of a directory, I do not need the entire system backed up. If I break something, I could fix it, or in worst case, reinstall the OS and reinstall my home partition contents.

---

### Post by crobruncato on 2010-05-28
> **Cope57 said:**
> A separate partition for /home has always done well as my backup.
A simple create archive of /home like cope57.tar.gz and move it to another PC or uploaded to a webserver has always been my best backup.

Other ways to backup could be applications like afbackup, amanda-client, backup2l, backup-manager, backupninja, backuppc, bacula, cedar-backup2, chiark-backup, dar, dirvish, faubackup, hdup, keep, and so on...

There are numerous ways to backup a system or files, you need to decide which works best for you. I only need a backup of a directory, I do not need the entire system backed up. If I break something, I could fix it, or in worst case, reinstall the OS and reinstall my home partition contents.

Been away for a while. Sorry to take so long to respond.

I'm sure many people on this forum can backup and restore their computer- that's not the point. Ubuntu is becoming, as Jerry Pournelle calls it "Aunt Millie's Linux" - which is a good thing. I'd say it needs easy backups and restores. If you have played with windows 7, it's backup and restore is easy. I hate to use windows as an example - but windows 7 backup is the example.

---

### Post by jerenept on 2010-05-28
BackInTime. great, effective, simple.

---

### Post by libssd on 2010-06-16
I would like to re-emphasize the OP. In the brief time I've been on the Ubuntu Forums, I have seen large numbers of "Help, I just installed XX, and now my system is hosed" messages. 

Ubuntu desperately needs a **simple**, reliable backup utility that can create a bootable system image on a HDD, USB, or optical drive as part of the standard distribution. Such programs exist, but they aren't always easy to find, or use -- something needs to be delivered with Ubuntu, preferably installed, or at least installable from the standard repository.

---

### Post by admiralspark on 2010-06-16
Just so you know, there are several threads concerning this exact subject already created on the forums. I do agree, but it get's old hearing the same thing after awhile. *Ahem* [Linux is Not Windows!!]("http://linux.oneandoneis2.org/LNW.htm")

Having said that, I'm going to insert my Linux Mint promotion for the day with their [Mint 9 (Isadora) Backup Tool]("http://www.linuxmint.com/rel_isadora_whatsnew.php#mintbackup"). It's very straightforward, easy to use, and made of the same quality construction as the rest of their Ubuntu spinoff. Heck, have a look at the rest of that page for other cool new features.

---

### Post by bodhi.zazen on 2010-06-16
Moved to T&E as this did not seem to be a support thread and T&E seemed better then the Cafe =)

The backup and restore features of Windows are not so great, they may seem simple, but they  are not reliable as you project in your original post, at least in my experience.

My suggestions are:

1. Before you update ANY OS, windows or Linux, you should look at what is being done to the system and make sure it makes sense.

2. Keep a separate /home or /data partition. By keeping your data separate from the Os it is a simple matter to re-install.

3. The new file system, btrfs, may offer the features you want. Such a system has been implemented in Fedora.

[http://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs](http://fedoraproject.org/wiki/Features/SystemRollbackWithBtrfs)

[http://www.phoronix.com/scan.php?page=news_item&px=Nzg5MA](http://www.phoronix.com/scan.php?page=news_item&px=Nzg5MA)

It is still in development, but you may want to check it out.

---

### Post by Sef on 2010-06-18
Moved to recurring discussion.  This is not a new subject.

---

