---
title: "Partition Question(Resize)"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by kuxpac383 on 2008-06-06
First off, I am running 8.04 on a Dual-boot(w/XP). During my original install I partitioned Ubuntu for 20GB, and left the rest for XP.  However, I want to resize my original partition for Ubuntu to be larger.  I have shrunk my XP by another 20GB and want to give that unallocated space to my Ubuntu filesystem.  I tried to do this with Gparted and Vparted but unable to do this.

My question is, can I resize this as of right now 20GB partition for Ubuntu and make it larger by adding an additional 20GB of unallocated space taken from XP?

OR 

Do I need to create another partition for this new 20GB space I created? 

Thanks, and best regards.

---

### Post by Paqman on 2008-06-06
Did you try to use Gparted while you were running your standard Ubuntu install? Because you can't make changes to any partition while it's mounted, which your root partition would have been.

If you boot into your LiveCD and try again your should have no problem.

---

### Post by iaculallad on 2008-06-06
When viewing your partitions with GParted, where is your NTFS partition located?
If you your NTFS is at the left-side and Ext3 on the right-side there is no chance for you to resize it.

---

### Post by rolnics on 2008-06-06
With my small experience of partition programs you should be able to merge similar partitions together. So long as they are the same file system type and are next to each other.

Another solution might be to create a new partition with this space and either use that as your /home or just mount it as separate.

---

### Post by kuxpac383 on 2008-06-06
[IMGhttp://i26.tinypic.com/zydde1.png[/IMG]

This is how it looks on Gparted.  I also tried to resize it using Parition Manager before my OS booted up. 

sda/7 is the one I want to make larger.

---

### Post by kuxpac383 on 2008-06-06
[IMG]http://i26.tinypic.com/zydde1.png[/IMG]

---

### Post by Paqman on 2008-06-06
> **iaculallad said:**
> 
If you your NTFS is at the left-side and Ext3 on the right-side there is no chance for you to resize it.

Gparted has been able to resize partitions in both directions for a while now.

You'll need to resize your extended partition into the free space and move your swap to the left. Then you can expand and/or move your ext3 partitions.

Just out of interest, what is your 2GB ext3 partition (sda6)? A small /home? And you've also got a 1GB NTFS partition. If those aren't doing anything useful you might as well get rid of them while you're in there playing about.

---

### Post by kuxpac383 on 2008-06-06
> **rolnics said:**
> With my small experience of partition programs you should be able to merge similar partitions together. So long as they are the same file system type and are next to each other.

Another solution might be to create a new partition with this space and either use that as your /home or just mount it as separate.


Well I would prefer to have one home partition, if possible.  So I would have to create another partition and merge them together?

---

### Post by iaculallad on 2008-06-06
> **Paqman said:**
> Gparted has been able to resize partitions in both directions for a while now.

My error, I had no update with GParted's updated feature. Since what version of Gparted enabled the resize of partition on both directions?

---

### Post by rolnics on 2008-06-06
> **Paqman said:**
> Gparted has been able to resize partitions in both directions for a while now.

Gparted will resize, but looking at your screenshot you've got the swap partition and a couple of other partitions in the way. It doesn't look like you'll be able to add that space to the Ubuntu partition. Probably the only solution I can think of is a new install, but maybe someone else has a better solution?

---

### Post by kuxpac383 on 2008-06-06
> **Paqman said:**
> Gparted has been able to resize partitions in both directions for a while now.

You'll need to resize your extended partition into the free space and move your swap to the left. Then you can expand and/or move your ext3 partitions.

Just out of interest, what is your 2GB ext3 partition (sda6)? A small /home? And you've also got a 1GB NTFS partition. If those aren't doing anything useful you might as well get rid of them while you're in there playing about.


When I created the partition for Ubuntu from Wubi the instructions I had said to create three partitions.  One for the swap, my main home filesystem(the 20GB home), and the other 2GB(sba6) I don't really remember why it told me to do it, but it did.

The NTFS partition is a backup HP created.  I don't really want to delete that one, just in case.

---

### Post by Paqman on 2008-06-06
> **iaculallad said:**
> My error, I had no update with GParted's updated feature. Since what version of Gparted enabled the resize of partition on both directions?

Looks like it was introduced in 0.3

[Gparted 0.3 changelog](http://sourceforge.net/project/shownotes.php?release_id=444805&group_id=115843)

---

### Post by Paqman on 2008-06-06
> **kuxpac383 said:**
> When I created the partition for Ubuntu from Wubi the instructions I had said to create three partitions.  One for the swap, my main home filesystem(the 20GB home), and the other 2GB(sba6) I don't really remember why it told me to do it, but it did.


Ok, can you please post the contents of your /etc/fstab file? It's possible that you might not be using sda6 for anything at all.

---

### Post by kuxpac383 on 2008-06-06
> **Paqman said:**
> Ok, can you please post the contents of your /etc/fstab file? It's possible that you might not be using sda6 for anything at all.

I apologize, but I don't know how to do this.

---

### Post by Paqman on 2008-06-06
> **kuxpac383 said:**
> I apologize, but I don't know how to do this.

Just navigate to it in the file manager and click on it, then copy the contents into a post here.

---

### Post by kuxpac383 on 2008-06-06
> **Paqman said:**
> Just navigate to it in the file manager and click on it, then copy the contents into a post here.

[IMG]http://i31.tinypic.com/2z52jyb.png[/IMG]

---

### Post by Paqman on 2008-06-06
FYI, that file shows what parts of the filesystem are getting mounted to what disk partitions

Since nothing is mounted on /dev/sda6 you can see that you aren't using it. So you can go ahead and delete it when you do your partition resizing/moving.

Btw, in future you might find it easier to just copy/paste things into a post. There's no need to go to all the trouble of making a screenshot just for text.

---

### Post by kuxpac383 on 2008-06-06
> **Paqman said:**
> FYI, that file shows what parts of the filesystem are getting mounted to what disk partitions

Since nothing is mounted on /dev/sda6 you can see that you aren't using it. So you can go ahead and delete it when you do your partition resizing/moving.

Btw, in future you might find it easier to just copy/paste things into a post. There's no need to go to all the trouble of making a screenshot just for text.

Ok thanks, well i just want to make sure you can see everything as I see it.  I am prone to making mistakes typing this late at night. Thanks for the help, the girlfriend is bugging me so I'll have to continue this at a later time.

---

### Post by oedha on 2008-06-06
AFAIK...when you run ubuntu you can't resize it
why dont you try to use gparted liveCD from [http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

