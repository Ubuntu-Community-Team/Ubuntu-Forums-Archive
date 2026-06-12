---
title: "Whats The Best Backup Option?"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by nakama85 on 2008-12-02
I have 2 internal hard drives. My 500 G Sata Has Ubuntu on it. 
My 180 G basically has no use at the moment. 
I was considering using it for Vbox and but I don't think I need that much room for it and I don't know if there is any benefit to doing this.

So I was wondering should I use it for Vbox and partition part of it for backup, should I Ghost to it or should  just use it to back up my home partition and as extra storage for movies and music? 

Thanks for any advice

---

### Post by nhasian on 2008-12-02
sbackup is an easy to use backup software with a gui.  you should look into rsync as well.

---

### Post by nakama85 on 2008-12-02
> **nhasian said:**
> sbackup is an easy to use backup software with a gui.  you should look into rsync as well.

Thanks. however if you had my setup what would be your choice of my above options?

---

### Post by Paqman on 2008-12-02
> **nakama85 said:**
> Thanks. however if you had my setup what would be your choice of my above options?

Well, you've got 180GB to play with, which is a lot.

Personally, i'd suggest that the most important things to back up are, in order:

[LIST=1]
[*]Your data
[*]Your /home folder
[*]The rest of the system
[/LIST]

So you'll need to have a look at how much data you need to back up, and then see how much other stuff you can fit into your 180GB.

You could set sbackup to automatically create archives including whatever folders you like. Just keep an eye on what it does to make sure it doesn't chew up all your storage if you have the settings a bit wonky. Alternatively you could just do manual backups using Grsync whenever you feel like. The traditional option is to learn how to use rsync on the command line and then set that up as a cron job, so that it will run automatically like sbackup does.

---

### Post by nakama85 on 2008-12-02
> **Paqman said:**
> Well, you've got 180GB to play with, which is a lot.

Personally, i'd suggest that the most important things to back up are, in order:

[LIST=1]
[*]Your data
[*]Your /home folder
[*]The rest of the system
[/LIST]

So you'll need to have a look at how much data you need to back up, and then see how much other stuff you can fit into your 180GB.

You could set sbackup to automatically create archives including whatever folders you like. Just keep an eye on what it does to make sure it doesn't chew up all your storage if you have the settings a bit wonky. Alternatively you could just do manual backups using Grsync whenever you feel like. The traditional option is to learn how to use rsync on the command line and then set that up as a cron job, so that it will run automatically like sbackup does.

Thanks, I think I will give all of the above a try so I can get a feel of things

---

### Post by kansasnoob on 2008-12-02
I personally love partimage!

I use it to create full backups to external drives all the time!

I've never had it fail!

---

### Post by nakama85 on 2008-12-02
> **kansasnoob said:**
> I personally love partimage!

I use it to create full backups to external drives all the time!

I've never had it fail!

It does ok with internal as well? I would assume but I figured I would ask anyway.

---

### Post by baruch60610 on 2008-12-02
I think your *best* option would be to put your backup files somewhere other than on a disk in the same box with your system.  If something happens to the box, it could easily trash both disks, making backups useless.

Having said that, it's still better to use the spare drive for backups.  There is a program called "keep" that seems to do a good job of making simple backups.  You can get it from one of the package managers (aptitude, synaptic, etc.).

---

### Post by nakama85 on 2008-12-03
hey. When I try to backup my home folder using KEEP I get this error > Fatal Error: Destination directory /home/uname/Backup exists, but does not look like a rdiff-backup directory. Running rdiff-backup like this could mess up what is currently in it. If you want to update or overwrite it, run rdiff-backup with the --force option.

Any Ideas

---

