---
title: "Advice in partitioning my PC."
date: 2013-01-31
forum: New to Ubuntu
---

### Post by whitefish10 on 2013-01-31
Hi guys, I want to partition my PC according to the following plan. 


[LIST]
[*]320 GB HD : / "root"
[*]1.5 TB HD : /home
[*]500 GB + 500 GB (Hardware RAID 1).
[/LIST]
My system is :-



[LIST]
[*]Core i5
[*]4 GB RAM
[*]Gigabyte GA-P67A-UD3-B3
[/LIST]
My questions are :-



[LIST=1]
[*]Fist is my plan good? any advise? I have arranged it according to my need.
[*]After the RAID 1 is enabled and active. How can I mount it and use it? with the name is /raid_data possible?
[/LIST]
Please advise me, and thank you.

---

### Post by Impavidus on 2013-01-31
You may want to add a swap partition to that. If you've got loads or RAM and don't hibernate your computer you don't really need it, but with plenty of disk space you won't miss a few GB. Otherwise, it seems fine. I don't think you will ever fill a 320GB root partition, but then again, I won't fill a 320GB drive anyway.

---

### Post by oldos2er on 2013-01-31
320GB for / more than ten times bigger than you would probably need. Mine is 26GB, and it's about half full (and I usually install a lot of programs).

---

### Post by fantab on 2013-01-31
15-25 GB for '/' is all you will need... Ubuntu actually installs on less than 9 GB with most of the software you will ever need.... 

remember to create as separate SWAP partition, if you will hibernate your computer than the SWAP should be equal to the system memory (RAM) in GiB...

Good Luck

---

### Post by vgezer on 2013-01-31
Why should we need to seperate partitions for both /home and / ?

---

### Post by Impavidus on 2013-01-31
You don't have to. Separate / and /home can be useful when reinstalling, moving to a new machine etc. because it's easy to keep your /home whilst reinstalling /, especially if you collect hundreds of GB in /home (which I don't). If you have multiple disks and don't want to make things complicated you have multiple partitions anyway, so why not make the biggest of them /home?

---

### Post by blackbird34 on 2013-01-31
+1
Then you can, say, keep your /home partition on the 320gb hdd and then use the 1.5tb one for backups, film and music collections, etc. Less messing about and you'd also be able to plug the big one into someone else's computer if you wished to IMHO

---

### Post by Bucky Ball on 2013-01-31
/ = 15Gb
/home = big as you want
/swap = 2Gb. You forgot the swap in your original plan! 

Your original / partition is obscenely too huge! You have a separate /home so on / you have the base install (small) and enough room to install every app known to the free - as in FOSS - world. (An exagerration but there is so much space there you won't use. May as well be another partition for storage. 

All your personal data will be going on /home so you would get away with 10Gb or under for /, depending on how many apps you are intending to install and what you are going to do with the computer. ;)

---

### Post by varunendra on 2013-02-01
> **fantab said:**
> if you will hibernate your computer than the SWAP should be equal to the system memory (RAM) in GiB...
I'd like to add - hibernation function is disabled by default in 12.04 (probably in 12.10 too) as it was too buggy and caused problems to many users. Although it can be re-enabled using minor tweaks, it is recommended to check beforehand to see if it works fine for you (it didn't for my Asus X54C). The command to test hibernation -
```
sudo pm-hibernate
```
(You can even use this command as a permanent way to hibernate everytime you need)

That being said, 2GB, like Bucky ball suggested above, for swap is usually the best size if you are not going to use hibernation.

Also, if hibernation works for you and you wish to use it, make swap 'slightly larger' than RAM. I'd suggest 4.5 GB (4608 MB) for your setup.

---

### Post by Bucky Ball on 2013-02-01
> **varunendra said:**
> 
also, if hibernation works for you and you wish to use it, make swap 'slightly larger' than ram. I'd suggest 4.5 gb (4608 mb) for your setup.

+1

---

### Post by vgezer on 2013-02-01
> **Impavidus said:**
> You don't have to. Separate / and /home can be useful when reinstalling, moving to a new machine etc. because it's easy to keep your /home whilst reinstalling /, especially if you collect hundreds of GB in /home (which I don't). If you have multiple disks and don't want to make things complicated you have multiple partitions anyway, so why not make the biggest of them /home?

> +1
Then you can, say, keep your /home partition on the 320gb hdd and then use the 1.5tb one for backups, film and music collections, etc. Less messing about and you'd also be able to plug the big one into someone else's computer if you wished to IMHO

Thank you for answers. If I seperate, then I could just remove / partition and install OS again, right? So I will not need to backup my music etc.

What about applications? There are so many bin directories. usr/local/bin and usr/bin (if i remember correctly).
Can backing up these directories keep our apps or anyway to export the list of apps (not from software center. e.g. to a text file)

---

### Post by oldfred on 2013-02-01
This is just a text file. If reinstalling the same version it should be fine. If a newer version you may want to edit out some old kernels or obsolete applications if new version uses different one. I run this as part of my rsync backup so I have the list to reinstall.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

    
       and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

   But do not just import all sources as that can lead to issues of versions:
[http://askubuntu.com/questions/2038/backup-software-sources](http://askubuntu.com/questions/2038/backup-software-sources)
sudo cp /etc/apt/sources.list ~/sources.list.backup
Otherwise if you have added any PPAs or other sources, the tip will only reinstall Ubuntu files,

---

### Post by vgezer on 2013-02-09
Sorry for late answer. Thank you. This was great explanation.

---

