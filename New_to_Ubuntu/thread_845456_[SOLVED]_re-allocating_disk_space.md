---
title: "[SOLVED] re-allocating disk space"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by gflujan on 2008-06-30
[color="red"][size="2"]**sorry if this thread is in the wrong place. I didn't really know where to post this.**[/size][/color]

here is my dilemma/situation:

I recently installed Ubuntu 8.04 as a dual-boot on my main HD (along with Windows XP). everything went fine but afterward I realized that I had made the partition bigger than I wanted. so after some searching, I learned that I could use GParted from the Ubuntu LiveCD to change the partition size. that worked fine however it didn't completely accomplish what I wanted. I was hoping that the extra space from re-partitioning Ubuntu would automatically be re-allocated to Windows.

what can or do I need to do in order to assign that extra space back to Windows???

thanks. :)

---

### Post by hyper_ch on 2008-06-30
you need to enlarge windows now with freed space... or rather the ntfs partition... however that freed space must be next to it...

---

### Post by rxtx on 2008-06-30
Yes, boot with the live CD, use gparted and increase the size of your NTFS partition to fill the newly available unused space.

---

### Post by sayakb on 2008-06-30
A partition can be expanded only if it has contiguous free space. Suppose if /dev/sda1 is Windows and /dev/sda2 is Ubuntu. Now these two partitions are contiguous. So in order to extend /dev/sda1 at the end, you have to shrink /dev/sda2 at the **beginning** which would leave free space that would be contiguous to the Windows partition. Where did you resize the drive from? Does your Windows partition have contiguous space? You may provide a screenshot of the gparted screen showing the partition map.

---

### Post by billgoldberg on 2008-06-30
> **LinuxIsInnovation said:**
> A partition can be expanded only if it has contiguous free space. Suppose if /dev/sda1 is Windows and /dev/sda2 is Ubuntu. Now these two partitions are contiguous. So in order to extend /dev/sda1 at the end, you have to shrink /dev/sda2 at the **beginning** which would leave free space that would be contiguous to the Windows partition. Where did you resize the drive from? Does your Windows partition have contiguous space? You may provide a screenshot of the gparted screen showing the partition map.

Yes, I remember a certain gparted resizing horror story from a few months back.

[http://ubuntuforums.org/showthread.php?t=762685&highlight=gparted&page=6](http://ubuntuforums.org/showthread.php?t=762685&highlight=gparted&page=6) (2nd last post).

---

### Post by gflujan on 2008-06-30
> **LinuxIsInnovation said:**
> A partition can be expanded only if it has contiguous free space. Suppose if /dev/sda1 is Windows and /dev/sda2 is Ubuntu. Now these two partitions are contiguous. So in order to extend /dev/sda1 at the end, you have to shrink /dev/sda2 at the **beginning** which would leave free space that would be contiguous to the Windows partition. Where did you resize the drive from? Does your Windows partition have contiguous space? You may provide a screenshot of the gparted screen showing the partition map.
here is the screenshot of what GParted sees:

[IMG]http://i5.photobucket.com/albums/y193/FreakMullet/internetForum/gParted_dskSpc.png[/IMG]

when I originally resized the partition, it wouldn't let me select /dev/sda2. so I chose to resize the /dev/sda5 partition.

---

### Post by sayakb on 2008-06-30
LOL... One of my friends starter gparted on an Inspiron 1520. Luckily, gparted finished partitioning in just 8 hrs.. 

> *[SIZE=2]ps: I disabled compiz fusion and thus emerald, I normally never use those ulgy windows borders[/SIZE]*[SIZE=2]
:lolflag: Classic
[/SIZE]

---

### Post by Elfy on 2008-06-30
> **billgoldberg said:**
> Yes, I remember a certain gparted resizing horror story from a few months back.

[http://ubuntuforums.org/showthread.php?t=762685&highlight=gparted&page=6](http://ubuntuforums.org/showthread.php?t=762685&highlight=gparted&page=6) (2nd last post).

I saw _re-allocating disk space_ and then I saw _billgoldberg_ and I remembered exactly the same thing :D

---

### Post by sayakb on 2008-06-30
Right click on /dev/sda1 and select **Resize/Move**. Can you move the slider to right to expand the space? If not, then /dev/sda1 being the primary partition and /dev/sda2 being extended it the culprit.

---

### Post by gflujan on 2008-06-30
> **LinuxIsInnovation said:**
> Right click on /dev/sda1 and select **Resize/Move**. Can you move the slider to right to expand the space? If not, then /dev/sda1 being the primary partition and /dev/sda2 being extended it the culprit.
no, I cannot move or resize /dev/sda1 at all. :( what do you mean that /dev/sda2 is the culprit?

should I just backup, "uninstall" Ubuntu and then reinstall it again???

---

### Post by uidb4056 on 2008-06-30
You have to resize /dev/sda2 selecting it and moving the left slider to right, then you can increase the size of /dev/sda1

---

### Post by Elfy on 2008-06-30
If yu are trying to resize sda1 to include the unallocated, then you are going to have to shrink the extended partion sda2 then the unallocated space should be outside the extended partion and you will be able to add it to sda1.

However you will not be able to do so from within ubuntu - you will have to either boot with the livecd and use partition editor in there, or use a bootable editor like partedmagic or gparted.


Edit - also it is likely that you will need to unmount the swap in the buntu livecd as it will use the swap.

---

### Post by kansasnoob on 2008-06-30
Just a reminder, you need to use a live CD to effectively change the size/position of partitions. You either can't do it using Gparted from your mounted Ubuntu OS or you'll be very, very sorry if you did!

Since you want to shrink sda1 (the windows partition), at least that's what I think you want to do, you need to first be sure that windows is shut down properly.

What I'd suggest is booting to Windows. I assume you get the GRUB screen at restart to do that. Then follow these steps (after you've backed up all important info, which we all do on a regular basis, eh?:

#1. Create a new restore point.
#2. Clean up! Time to trash the temp files and other garbage! If you haven't run an Anti-Virus scan this would be a good time to do it. I like AVG free.
#3. Defrag! You must defrag! Windows is terrible about scattering data from one end of a partition to another!

Then use Gparted to shrink that partition!

---

### Post by gflujan on 2008-06-30
> **kansasnoob said:**
> Just a reminder, you need to use a live CD to effectively change the size/position of partitions. You either can't do it using Gparted from your mounted Ubuntu OS or you'll be very, very sorry if you did!

Since you want to shrink sda1 (the windows partition), at least that's what I think you want to do, you need to first be sure that windows is shut down properly.

What I'd suggest is booting to Windows. I assume you get the GRUB screen at restart to do that. Then follow these steps (after you've backed up all important info, which we all do on a regular basis, eh?:

#1. Create a new restore point.
#2. Clean up! Time to trash the temp files and other garbage! If you haven't run an Anti-Virus scan this would be a good time to do it. I like AVG free.
#3. Defrag! You must defrag! Windows is terrible about scattering data from one end of a partition to another!

Then use Gparted to shrink that partition!
I don't want to shrink /dev/sda1, I just want to be able to allocate the unused disk space (from shrinking sda2) back to Windows.

---

### Post by gflujan on 2008-06-30
> **forestpixie said:**
> If yu are trying to resize sda1 to include the unallocated, then you are going to have to shrink the extended partion sda2 then the unallocated space should be outside the extended partion and you will be able to add it to sda1.

However you will not be able to do so from within ubuntu - you will have to either boot with the livecd and use partition editor in there, or use a bootable editor like partedmagic or gparted.


Edit - also it is likely that you will need to unmount the swap in the buntu livecd as it will use the swap.
well, GParted won't let me resize/move sda2 to move the unallocated space outside of it.

should I just uninstall everything???

---

### Post by Elfy on 2008-07-01
Are you doing it from the livecd?

Because you have to - while sda2 is mounted you can't resize it - thereofre you can't free the space to add it to sda1

---

### Post by gflujan on 2008-07-01
> **forestpixie said:**
> Are you doing it from the livecd?

Because you have to - while sda2 is mounted you can't resize it - thereofre you can't free the space to add it to sda1
yes, I've been trying from the LiveCD. however, the only options that I get when I select/right-click on it are "Manage Flags" and "Info/Properties".

is QTParted a better program than GParted???

---

### Post by Elfy on 2008-07-01
Never used itr so couldn't say - but run this command and then have another go

```
sudo swapoff -a
```

You need to have all partitions unmounted - swap was mounted.

---

### Post by gflujan on 2008-07-01
> **forestpixie said:**
> Never used itr so couldn't say - but run this command and then have another go

```
sudo swapoff -a
```

You need to have all partitions unmounted - swap was mounted.
awesome, that seems to have worked. thank you. :D

---

### Post by Elfy on 2008-07-01
It's well worth getting a copy of gparted or partedmagic and supergrub burnt for lifes little emergencies.

I prefer to use partedmagic now after a few hiccups - get them downloaded, burn as iso's and they will be ready fornext time.

If you're happy and done could you mark thread solved and finally, you're welcome.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by gflujan on 2008-07-01
> **forestpixie said:**
> It's well worth getting a copy of gparted or partedmagic and supergrub burnt for lifes little emergencies.

I prefer to use partedmagic now after a few hiccups - get them downloaded, burn as iso's and they will be ready for next time.

If you're happy and done could you mark thread solved and finally, you're welcome.

[http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads](http://partedmagic.com/wiki/PartedMagic.php?n=PartedMagic.Downloads)
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
is there a way to mark the thread as solved??? or do I just type it into the title???

---

