---
title: "Backing up Windows"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Dadof4 on 2011-09-17
I am running Ubuntu and Windows on two separate drives as a dual boot. My Windows drive (320gb)is starting to fail and I need to do a backup, is there any way to back up to my Ubuntu drive (1 Tb)?

---

### Post by P05TMAN on 2011-09-17
> **Dadof4 said:**
> I am running Ubuntu and Windows on two separate drives as a dual boot. My Windows drive (320gb)is starting to fail and I need to do a backup, is there any way to back up to my Ubuntu drive (1 Tb)?

It seems that there is a way, I found this link describing how: 
[http://www.thheuer.com/2011/08/how-to-backup-windows-xp7-partition-with-linux-ubuntu/](http://www.thheuer.com/2011/08/how-to-backup-windows-xp7-partition-with-linux-ubuntu/)

---

### Post by Rubi1200 on 2011-09-17
Personally, I think Clonezilla would be a better option:
[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by haqking on 2011-09-17
> **Rubi1200 said:**
> Personally, I think Clonezilla would be a better option:
[http://clonezilla.org/](http://clonezilla.org/)

+1

But a backup and a clone are different as a Backup can have incremental changes over time enalbing a restore easier, where as a Clone is a fixed image of a given moment.

However i think what you are asking is for a backup of your Windows build ? or just your personal data ?

If it is just your personal data then copy it onto a externall HDD maybe and then restore to your /home in ubuntu.

BUt having a clone of your existing is good so that if you trash your sytem somehow installing Ubuntu you cna just clone the old system back how it was.

---

### Post by CharlesA on 2011-09-17
> **Rubi1200 said:**
> Personally, I think Clonezilla would be a better option:
[http://clonezilla.org/](http://clonezilla.org/)

+1

> **haqking said:**
> +1

But a backup and a clone are different as a Backup can have incremental changes over time enalbing a restore easier, where as a Clone is a fixed image of a given moment.

However i think what you are asking is for a backup of your Windows build ? or just your personal data ?

If it is just your personal data then copy it onto a externall HDD maybe and then restore to your /home in ubuntu.

BUt having a clone of your existing is good so that if you trash your sytem somehow installing Ubuntu you cna just clone the old system back how it was.

+1.

If the HDD is failing, I'd not worry about cloning the drive and just pull the files over from a livecd. Of course you can also clone the drive and pull the files from that but it's your choice.

---

### Post by Mark Phelps on 2011-09-17
If you're running Windows 7, then BEFORE it fails completely, do yourself a favor and use the Backup feature to create and burn a Win7 Repair CD.  This will enable you to repair the boot loader and get it working again -- after you save it off and restore it to a new drive.

---

