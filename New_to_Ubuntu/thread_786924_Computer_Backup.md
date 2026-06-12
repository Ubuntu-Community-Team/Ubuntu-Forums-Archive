---
title: "Computer Backup"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by G!zZm0 on 2008-05-08
Is there any specific program I can use to backup all my computer files???

---

### Post by hessiess on 2008-05-08
if you have 2 computers or 2 hard drives unison or RSync can backup files from one to the outher.

---

### Post by ugm6hr on 2008-05-08
I use Grsync - simple GUI for rsync

---

### Post by quelx on 2008-05-08
**sbackup** is nice because it create incremental backups so if you make a mistake you can go back to previous versions of your file (think Apple's Time Machine w/o the fluff)

---

### Post by tamoneya on 2008-05-08
I use sbackup as well.  I am backing up both my desktop and my laptop to my ssh server daily and it works flawlessly.  Took a little while to configure but I have it figured out now.

---

### Post by abhiroopb on 2008-05-08
I personally like to use partimage. Basically when I want to backup (about weekly) I delete my music folder (about 40gb), and I clean out my system. Then use partimage (more information on how to use it here: [http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)). This way if I ever have a problem I can just restore the image and I don't have to configure anything.

---

### Post by OMRebel on 2008-05-08
I use TimeVault.  Very easy to use program, and does a fantastic job.  I haven't tried any others, so I don't know if it's better than the others, but for me, it has worked great and is just easy to use.

Whatever you decide to use, make sure you backup your /home and /etc.

---

### Post by kansasnoob on 2008-05-08
abhiroopb does things just like I do.

Partimage is very, very simple and straight forward.

One thing though: any partition you create a backup of must be unmounted, so you may very well be better off using Partimage from a Systenm Rescue CD or any Live CD that has Partimage.

I just did my first restore of an XP partition this morning and I was surprised at how easy it was ........ well until I got to the authentication process but that's a windows nightmare.

---

### Post by abhiroopb on 2008-05-09
> **kansasnoob said:**
> abhiroopb does things just like I do.

Partimage is very, very simple and straight forward.

One thing though: any partition you create a backup of must be unmounted, so you may very well be better off using Partimage from a Systenm Rescue CD or any Live CD that has Partimage.

I just did my first restore of an XP partition this morning and I was surprised at how easy it was ........ well until I got to the authentication process but that's a windows nightmare.


Good point, I forgot to mention that you should use system rescue cd (found here: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)).

Last night I discovered sbackup. It actually is very easy to use. And after I excluded all my big media files (pictures/music). I only had about 2gb of data (as it is tarred). So I thought I'd use sbackup as well. Yes I am very paranoid. So. I have a 60gb portable hard disk, split into two ext3 partitions. One for the partimage stuff, and one for the sbackup (which does daily backups). In addition I backup my VERY important documents (such as essays, revision notes) on a pen drive which I carry around everywhere with me (in case I need it!).

---

### Post by abhiroopb on 2008-05-09
I looked into TimeVault. I personally found that its a bit klunky to use. Let me put it this way. I installed sbackup (it was in the package manager). And had a customised backup set up to take place every day, and within 15 minutes my backup configurations were set and the first backup was done.

With timevault, I installed it, and at first couldn't find it in any of the menus. Then I used gnome do, and it had been indexed. So I launched it. I set up the preferences and it didn't really do anything. I waited a bit, and I couldn't figure out how to do a backup. It said it had nautilus integration (one of the options in the preferences), yet I could not figure out HOW it integrated. Anyway I guess I'd have to fiddle around with it more. But I only need to backup about 2-3gb of important data and sbackup does a wonderful job of this. Its quick, effecient, and I barely notice its running (just at some point in the day I see the light flashing on my hard drive for a brief period).

---

### Post by hyper_ch on 2008-05-09
I use rsync to make a incremental snapshot-style backup every 6h dating back for 90 days.

---

### Post by abhiroopb on 2008-05-11
Sbackup is simply amazing, does exactly what I need, although restoring individual files can take upto 4 minutes. Just wondering though, I have a 60gb external hard drive to backup my data. I keep it connected through USB 2.0. I can hear it spinning all the time. I do a backup daily (its automatic). However, I don't want the external hard drive to be spinning all the time my computer is on (which is most of the time). Is there anyway to automatically spin down the hard drive when it isn't being used? (its ext3 formatted)

---

