---
title: "[SOLVED] Ubuntu forgets a partition on my hard drive"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by kingdonerkebab on 2008-10-16
Hi. Only installed Ubuntu a few days ago so maybe I'm being stupid.  

I created a separate partition to install Ubuntu on, so I've got 3 partitions, one for vista home premium, one with all my music files, pictures, videos etc and one with Ubuntu. I want to change the Places menu so the music folder links directly to the music folder on my other drive, but when I move the folder in there with nautilus, it only stays there until I reboot then disappears. If I find music folder by another route then look at the menu again it reappears. I feel like it's the same problem I'm having with Amarok; 

In Amarok I go to settings>configure amarok>collection and when I follow the highlighted folders down to where I set it to look for my music (should be />media>data>music), the highlighted folders only go down to />media with just an empty space where "data" should be.

It's only a small problem, but just slightly annoying, and I'm sure there must be some way to solve this. I would greatly appreciate any help on getting Ubuntu to recognize the other partition on my drive.

Thanks.

---

### Post by vanadium on 2008-10-16
I guess your second partition, where your music is, is ntfs or fat formatted. Since the latest version of Ubuntu, such partitions are only mounted "on demand". I guess it is because of this 'new' way of mounting the volumes that you have these issues. You would better mount these drives 'the traditional' way, i.e. by declaring the partitions in /etc/fstab. A nice guide for that is here: [http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by kingdonerkebab on 2008-10-16
Thanks for the reply. The link you sent was a bit complicated for me but it led me on the right path 'til i found this simpler one.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20and%20checking%20the%20partitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Mounting%20and%20checking%20the%20partitions)

Am I right in thinking that NTFS drives can only be read-only in ubuntu at present?

Edit: I did what it says on this page and now the partition is read only whereas I could read and write on to it before. I think it's going to take me a little while before I get used to this.

---

### Post by egalvan on 2008-10-16
> **kingdonerkebab said:**
> Am I right in thinking that NTFS drives can only be read-only in ubuntu at present?

As of 8.04 (hardy), NTFS is fully read/write.

I use ntfs as my data partitions on my dual-boot machines...
no problems.

And I guess one reason that linux doesn't auto-mount ntfs on boot,
is that if XP does not shut down properly, the ntfs partitions will have th 'dirty-bit' set. Linux does not like 'dirty' ntfs partitions.
It IS possible to 'force' mount a dirty partition, but you run a higher risk of data loss.

Always do a correct shutdown of XP... reboot if needed.

And yeah, I find it slightly annoying to 'manually' mount ntfs every boot, but not so much that I've changed my fstab settings.

---

### Post by egalvan on 2008-10-16
> **kingdonerkebab said:**
> Edit: I did what it says on this page and now the partition is read only whereas I could read and write on to it before. I think it's going to take me a little while before I get used to this.

Here is another link...

[http://ubuntuforums.org/showthread.php?t=785263&highlight=automount+ntfs](http://ubuntuforums.org/showthread.php?t=785263&highlight=automount+ntfs)

and another with excellent information...this will help to further understand the different tutorials and tips you will find...

[http://ubuntuforums.org/showthread.php?t=283131&highlight=automount+ntfs](http://ubuntuforums.org/showthread.php?t=283131&highlight=automount+ntfs)

---

### Post by kingdonerkebab on 2008-10-16
Thankyou SO much. Those last links you posted were great. I was doing all sorts of things wrong. 

I've got to say though, I'm having quite a lot of fun fiddling about with things. I am spending quite a lot of time on my computer nowadays. Don't know if that's a good thing. :)

---

### Post by egalvan on 2008-10-16
> **kingdonerkebab said:**
> Thankyou SO much. Those last links you posted were great. I was doing all sorts of things wrong. 

I've got to say though, I'm having quite a lot of fun fiddling about with things. I am spending quite a lot of time on my computer nowadays. Don't know if that's a good thing. :)

Well, it can't be all bad if you are having fun...

And yeah, bodhi.zazen is great at explaining stuff...

Check out more of his stuff under the 'Tips & Tricks' sub-forum.
You can trust his advice. 

I use two older computers to 'play' with linux,
and have my 'work' machines separate.

keep on learning....

---

### Post by hagantic42 on 2008-10-22
Ok along the same lines as this guy I have a fat 32 storage partition but that is the ONLY one that won't auto mount. The NTFS config worked just fine on the two NTFS parts but now how do I do the fat 32 i assume i need to use good'ole fstab

---

### Post by Duck2006 on 2008-10-22
> but now how do I do the fat 32 i assume i need to use good'ole fstab

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

