---
title: "Imaging?"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by Yezinki on 2012-12-28
1. The machine running Ubuntu has a 320 GiB HDD.

2. 30 GB /, 263 GiB /home & approx 5 GiB swap.

3. Can I use Macrium or Acronis to image the whole Ubuntu or is there a better utilty for creating & restoring full backups?

4. Plan to resize /home, using GParted Live CD, to store fully created images.

Hoping to hear your expert views.

Thanks.

---

### Post by squakie on 2012-12-28
Not sure about Acronis, but Macrium never did backup up my non-dos, non-ntfs partitions - e.g. an Ubuntu partition.  I don't know if there are other drive imagers that will backup the entire drive and include all partitions regardless of type.  Just my experience with Macrium Reflect.

EDIT:  Just found this old post in their support forum that says it will backup ext2/ext3/ext4 partitions:   [http://support.macrium.com/topic.asp?TOPIC_ID=2113 ]("http://support.macrium.com/topic.asp?TOPIC_ID=2113")  I'm sure you know, but Macrium needs to be run in Windows, and I doubt it would work in Wine.[URL="http://support.macrium.com/topic.asp?TOPIC_ID=2113"]
[/URL]

---

### Post by cwsnyder on 2012-12-28
Look at Clonezilla (it is a boot disk). [http://clonezilla.org/](http://clonezilla.org/)

---

### Post by The Spectre on 2012-12-28
Acronis only seems to have a Linux Version for Linux Server and it is ridiculously expensive...
[http://www.acronis.com/backup-recovery/smallbusiness.html#ABR11-5SL](http://www.acronis.com/backup-recovery/smallbusiness.html#ABR11-5SL)

And Macrium Reflect appears to be designed with only Windows in mind.

What I have been using is Redo Backup & Recovery...
[http://redobackup.org/](http://redobackup.org/)
And it has saved me on more than one occasion.

---

### Post by audiomick on 2012-12-28
> **cwsnyder said:**
> Look at Clonezilla (it is a boot disk). [http://clonezilla.org/](http://clonezilla.org/)

I haven't used it, but from what I have read, this is a good tip.

---

### Post by kejava on 2012-12-28
Redo looks nice.  I haven't heard of that one before.  Says it's a front end to partclone which is similar to partimage.  I used partimage a while back until development of partimage seemed to stop and was move to a new project called [fsarchiver]("http://www.fsarchiver.org/Main_Page").  It's an ugly command line app but it does a great job and documentation is clear and easy to read.  Support for restoring to partitions of different sizes is nice.  It's fast.  They have a nice page [here]("http://www.fsarchiver.org/Fsarchiver_vs_partimage") that describes the differences between fsarchiver and partimage.

One thing that sucks is I haven't seen any backup utilities that include a simple solution for backup/restore of grub bootloader information.  Seen people us dd but it's best to just reinstall grub to the appropriate mbr or partition.  I'm insterested in any other responses you get.

---

