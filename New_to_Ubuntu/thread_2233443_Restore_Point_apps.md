---
title: "Restore Point apps"
date: 2014-07-08
forum: New to Ubuntu
---

### Post by paw2005 on 2014-07-08
Hi All,
What are the best Apps for creating a restore point similar to Windows XP
TimeShift? or other?
Thanks in advance for tips....
pete

---

### Post by Habitual on 2014-07-08
[backintime]("http://backintime.le-web.org/") perhaps?

---

### Post by hikuritamete on 2014-07-08
The best way is using Systemback:[URL="https://launchpad.net/~nemh/+archive/systemback"]
https://launchpad.net/~nemh/+archive/systemback[/URL]
[http://sourceforge.net/projects/systemback/](http://sourceforge.net/projects/systemback/)
sudo add-apt-repository -y ppa:nemh/systemback
sudo apt-get upate
sudo apt-get install  -y --force-yes systemback

---

### Post by Rob Sayer on 2014-07-08
Linux isn't designed for restore points as windows is.  It doesn't really work like windows ... actually it works more like a Mac because OS X is also a Unix derivative ... and I've never thought about trying to do that.

I especially wouldn't trust a 3rd party app from an untrusted ppa like the abovementioned tools.  There aren't any similar tools that I know of in the tested repos.  This isn't insignificant IMO.

---

### Post by monkeybrain20122 on 2014-07-08
> **Rob Sayer said:**
> 
I especially wouldn't trust a 3rd party app from an untrusted ppa like the abovementioned tools.  There aren't any similar tools that I know of in the tested repos.  This isn't insignificant IMO.

Why not? all ppas are 'untrusted', just a disclaimer from Canonical. I think OP should give it a try, but test it first with a test install in an external hd or a test partition.

Personally I just clone my / partition regularly with fsarchiver (about 12Gs both cloning and restore are fast)

---

### Post by philinux on 2014-07-08
There is an but it involves using the btrfs file system and using it's snapshot feature. 

Discussion here.
[http://askubuntu.com/questions/56095/how-i-do-a-system-restore](http://askubuntu.com/questions/56095/how-i-do-a-system-restore)

---

### Post by Mark Phelps on 2014-07-08
> What are the best Apps for creating a restore point similar to Windows XP

I'm guessing that you are under the misconception that Windows Restore Points allow you to restore the Entire Environment of a Windows machine to a former date -- a popular misconception.

Instead, what they really do is restore the Windows Operating System back to an earlier date, and they do that by overwriting current OS files and settings with those saved when Windows Updates were applied.

What Restore Points do NOT do is restore personal stuff or data back to an older date.

If what you really want, is a way to restore the entire environment to an earlier date, the way to do this is to use something like Clonezilla to image off your Linux partitions.  The same kind of stuff is done in the Windows world using products like Easeus, Acronis, and Macrium Reflect.

---

### Post by Vladlenin5000 on 2014-07-08
> **Mark Phelps said:**
> I'm guessing that you are under the misconception that Windows Restore Points allow you to restore the Entire Environment of a Windows machine to a former date -- a popular misconception.

Big +1

> If what you really want, is a way to restore the entire environment to  an earlier date, the way to do this is to use something like Clonezilla  to image off your Linux partitions.  The same kind of stuff is done in  the Windows world using products like Easeus, Acronis, and Macrium  Reflect.

Another big +1
And Clonezilla for Windows. Why not? It supports NTFS, does a fine job and it's FREE :p

---

### Post by Bucky Ball on 2014-07-08
Run Clonezilla as regularly as required to a backup disk and save the last two at all times. As explained, does an identical copy of your partition (or entire disk) which you can restore to ANY partition of the same size as the original or bigger (even on another machine). ;)

Possibly easiest and most complete once you have your head around using it. Here's some food for thought:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

---

### Post by monkeybrain20122 on 2014-07-08
If you are not using gpt and have only Linux OSes I would use fsarchiver instead of clonezilla. Easier and more flexible. What do you do with clonzilla if you have a big partition which is mostly empty? From Buckey Ball's link you should shrink the  partition before cloning as  you may have to restore to a smaller drive. So what to do after? expand it again in case you may have more stuffs in the future?

[http://www.fsarchiver.org/QuickStart](http://www.fsarchiver.org/QuickStart)

---

### Post by Mark Phelps on 2014-07-09
>  What do you do with clonzilla if you have a big partition which is mostly empty?

Well, first of all, you do NOT clone that partition -- that's not a sensible backup strategy.  Cloning is not a useful backup strategy unless you want/need the option of hot swapping installs.

Second, you would Image off that partition using Clonezilla, and it would end up taking a fraction of the space occupied by the actual partition. In this case, there is no need at all to shrink the original partition.

---

### Post by Bucky Ball on 2014-07-09
> **Mark Phelps said:**
> 

Second, you would Image off that partition using Clonezilla, and it would end up taking a fraction of the space occupied by the actual partition. In this case, there is no need at all to shrink the original partition.

^^^
This.

---

### Post by monkeybrain20122 on 2014-07-09
> **Mark Phelps said:**
> 
Second, you would Image off that partition using Clonezilla, and it would end up taking a fraction of the space occupied by the actual partition. In this case, there is no need at all to shrink the original partition.

The image is smaller but if you have to restore it you still need a partition at least as big as the source partition, that makes restoring to smaller destinations and re-partitioning of same drive (say I want to add an OS) inflexible.

I have no idea what you are talking about with the first point. Who says you should use cloning as a data backup strategy?

---

