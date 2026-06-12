---
title: "Unlocking partitions"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by CloudFX on 2008-04-21
Hi,

I have an extended partition which has been 'locked', and I am clueless at how to unlock it.  It's not mounted, and I've deleted all partitions inside of it to form unallocated space.  The partition is around 5gb.  Is there an input I can use to unlock it, or any other method?

---

### Post by SOULRiDER on 2008-04-21
After you removed the partitions, did you make a new one?

---

### Post by CloudFX on 2008-04-22
No, I kept it as unallocated.  I don't think that that is the problem.  I just need to know how to 'unlock' these partitions..

It goes like this, btw:

/dev/sda#
/dev/sda#
/dev/sda#
    unallocated space

---

### Post by zvacet on 2008-04-22
Boot with live CD and then you will be able to unlock partitions.

---

### Post by kansasnoob on 2008-04-22
You can only make very limited changes to partitions just by accessing GParted (partition editor) through the system menu. There's a great reason for this!

I've mistakenly deleted partitions without editing the GRUB menu and ended up with an un-bootable system. You must know how to "flag" the partitions, how to mark the partitions to be mounted, etc. If you're not sure ask more questions! Try just right clicking the partitions and look at the options and make some notes and don't be afraid to ask more questions.

But, if you're sure what you want to do in GParted then just access it with the Ubuntu Live CD ......... just boot the CD and choose to use it as a live CD.

After it's done booting just go to System>Administration>Partition Editor and you'll be able to change whatever you want, but be absolutely sure what you want!

When you're done just restart the computer.

Oh, quite often the partition editor will shut down after each change so keep restarting the partition editor until all changes are complete. (It's somewhat easier to do with a GParted live CD which you can easily find on line if you have the capability to burn one & it's small) ALWAYS AVOID SECOND PARTY DOWNLOADS! I like to use the live CD native to my Ubuntu system, but that's me.

If you're only messing with inactive partitions (ie:regaining space) you should be OK, but if you end up with an unbootable system then slip in your Ubuntu Live CD again, restart (usually works with ALT>CTRL>DLT), and then open the Terminal and type in: sudo grub

Then type in: find /boot/grub/stage1

You'll likely see: hd(0,0)

If so type in: root(hd0,0)

Then type in: setup(hd0)

Then type in: quit

Then type in: exit

When you reboot if you're not not up and running then you probably deleted a partition you shouldn't have.

The worst that will happen is having to reinstall Ubuntu ........... it's free, and each time you remember more of what you did the time before, and (in my case) you end up wondering why you ever used Windows to begin with!

And this new 8.04 just rocks!

---

### Post by mattywarr on 2008-04-22
> **zvacet said:**
> Boot with live CD and then you will be able to unlock partitions.

If you boot with LiveCD you won;t need to unlock them - you can just resize the partition you want to fill the empty space with (Which I assume your trying to do) 

Then apply the changes and reboot back to HDD and your partitions will be good.

---

### Post by CloudFX on 2008-04-22
That's not the problem.  I'm fully aware of the usage of GParted, GRUB, and Ubuntu, but the issue I have is one I've never seen before... I'll take a screenshot later on.

Thansk everyone!

---

### Post by J_holubek on 2008-08-21
> **mattywarr said:**
> If you boot with LiveCD you won;t need to unlock them - you can just resize the partition you want to fill the empty space with (Which I assume your trying to do) 

Then apply the changes and reboot back to HDD and your partitions will be good.

You say here, that when you are on the live cd that you do not have to unlock the partitions... and that you should be able to freely edit them... Why is this not the case with me? mine are still locked even if I am accessing them through the live CD..

---

### Post by b4sakenxx on 2008-10-24
way old thread but for future reference for anyone that stumbles on to this.
unmount the partition in gparted (doesn't need to be livecd version) by first choosing the partition, then click Partion -> Unmount in the menu.  you can then do whatever you want to it.

---

### Post by Lord_Vacuity on 2010-02-04
I am trying to install Ubuntu 9.10 using the liveCD but that partition I want to install into is locked.  I don't know how it got locked. I encountered this yesterday as well when I wanted to install another distro on that partition. I thought that maybe it was reading locked because it hadn't shut down properly so I rebooted that distro and then tried to install again but the partition still shows as being locked. 

Can anybody tell me how to unlock it?

---

