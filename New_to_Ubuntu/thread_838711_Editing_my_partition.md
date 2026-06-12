---
title: "Editing my partition"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by Fritooo on 2008-06-23
Okay, so when I partitioned for a dual boot, I only gave Linux like 30 gb out of my 80gb hd. Is there any way for me to either make that partition bigger and the windows one smaller, or even delete the windows one and give all of it to Linux? Cause I like Ubuntu enough to use it completely, but there's some data stored on Windows that I would like to keep.
I hope that made sense, help.

It would be fine if it didn't lag so much how I have it set up right now. I'm assuming this is the problem, as I have 2gb of memory and 3gb of swap.

---

### Post by Xerp on 2008-06-23
Yes, you can use GParted to resize any partition. There is even a GParted Live CD - greated for resizing partitions that would otherwise be "in use".

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Duck2006 on 2008-06-23
Or use parted magic, don't for get to Defragment the win drive first.

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

---

### Post by Rocket2DMn on 2008-06-23
You have to use either the Ubuntu LiveCD or the Gparted LiveCD - [http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/) to resize your root partition since you cannot fiddle with it while it is mounted.
Please make sure you backup your important data before resizing.  Although it is unlikely that it will break anything, there is always the possibility.

---

### Post by Fritooo on 2008-06-23
Thanks so much, the biggest problems have been that my Windows has some errors in it... that's what happens when the system32 gets deleted I suppose :D

Would it be possible to just transfer all the files I need from Windows and then delete it completely and give my Linux partition the full hard drive?

---

### Post by Xerp on 2008-06-23
Yes, that is totally possible. Again, GParted can be used to delete the unused Windows partition.

---

### Post by Rocket2DMn on 2008-06-23
> **Fritooo said:**
> Thanks so much, the biggest problems have been that my Windows has some errors in it... that's what happens when the system32 gets deleted I suppose :D

Would it be possible to just transfer all the files I need from Windows and then delete it completely and give my Linux partition the full hard drive?

Yes, you can delete the windows partition if you don't want it anymore.  Have a look here - [uhelp]community/HowToRemoveWindows[/uhelp]

---

### Post by Fritooo on 2008-06-23
When I try to adjust the size of the partition it always errors and says that it's mounted, even though I purposely unmount it before every try.
unallocated space is 46.57Gb, and my linux partition is 25.15 Gb, and located at /dev/sda2

Oh, and it's also only letting me make it smaller, instead of using the full unused space.

Help now?

---

### Post by louieb on 2008-06-23
You need to run GParted from a live CD. Thats how you get around the mount problem. 

Just wondering have you thought about leaving the partitions the same size they are and formating the old Windows partition ext3. Then you can use it just for data, music, photos and other stuff. You data will also be safe in case you have to reinstall.

---

### Post by Fritooo on 2008-06-24
I had thought about that, but I have an external hard drive for all of that stuff and have transferred everything I need to that.

Now my problem is that it's not letting me resize the Linux ext3 partition into the unused space ><

Edit:
[IMG]http://i32.tinypic.com/30iavq8.png[/IMG]

This is what my gpart window looks like.

Edit 2:
I think I figured out what to do. I'm going to copy the partition on the right into the left space, then delete it and extend the partition on the left all the way to the swap. If this won't work please tell me before I screw everything up.

---

### Post by linfidel on 2008-06-24
I see you have one operation pending - what is that?  Maybe you should try applying the last operation before continuing.

How are you running gparted?  from  CD?

I've had problems in the past where auto-mount was enabled, and I had to disable automount in order to use gparted.  But I forgot exactly where I did that.

---

### Post by Fritooo on 2008-06-24
I'm running it from ubuntu live cd.

---

### Post by Fritooo on 2008-06-24
ugh, when it's copying the volume it will auto mount randomly
how do i turn that off?

---

### Post by Rocket2DMn on 2008-06-24
I think the Ubuntu LiveCD mounts the swap partition which can cause problems.  You may want to try the GParted LiveCD mentioned earlier.

---

### Post by louieb on 2008-06-24
Growing a partition to the left like you want to do to sda2  will take forever and a day.  (literally it may take a day or more - GParted is not the fastest)   Much faster way. click on the unused space and create a new partition the same size as sda2. Then once created copy sda2 to it.   GParted has a copy function.

Then grow the new partition to the right. GParted is much faster copying partitions and growing it to the right. 

One problem you may run into doing it that way is the UUID of the new partition may be different.   You use the **blkid** command  to find the UUID of the partition. then two files will have to be updated with the new UUID** /boot/grub/menu.lst** and[B] /etc/fstab.  

[/B]Another thing you will have to do is use the GRUB command prompt to change the MBR to use GRUB on the new partition.  Takes 2 minutes if that long.

IF you hibernate the computer there is a 3rd file to update  if the swap files UUID changed **/etc/initramfs-tools/conf.d/resume. **

Even with having to update the files  manually it still faster.

---

### Post by Duck2006 on 2008-06-24
> **louieb said:**
> Growing a partition to the left like you want to do to sda2  will take forever and a day.  (literally it may take a day or more - GParted is not the fastest)   Much faster way. click on the unused space and create a new partition the same size as sda2. Then once created copy sda2 to it.   GParted has a copy function.

Then grow the new partition to the right. GParted is much faster copying partitions and growing it to the right. 

One problem you may run into doing it that way is the UUID of the new partition may be different.   You use the **blkid** command  to find the UUID of the partition. then two files will have to be updated with the new UUID** /boot/grub/menu.lst** and[B] /etc/fstab.  

[/B]Another thing you will have to do is use the GRUB command prompt to change the MBR to use GRUB on the new partition.  Takes 2 minutes if that long.

IF you hibernate the computer there is a 3rd file to update  if the swap files UUID changed **/etc/initramfs-tools/conf.d/resume. **

Even with having to update the files  manually it still faster.

+1 It will be faster to do it that way.

---

### Post by linfidel on 2008-06-24
> **louieb said:**
> ...
One problem you may run into doing it that way is the UUID of the new partition may be different.   You use the **blkid** command  to find the UUID of the partition. then two files will have to be updated with the new UUID** /boot/grub/menu.lst** and[B] /etc/fstab.  

[/B]Another thing you will have to do is use the GRUB command prompt to change the MBR to use GRUB on the new partition.  Takes 2 minutes if that long.

IF you hibernate the computer there is a 3rd file to update  if the swap files UUID changed **/etc/initramfs-tools/conf.d/resume. **

Even with having to update the files  manually it still faster.Actually, the copy will also copy the UUID, which can be a problem if you don't delete the original.  I was copying various partitions around a while back, and things got confused until I found this out.  But in this case,  it will be an advantage, as the grub menu won't need to be changed.

---

### Post by avtolle on 2008-06-24
You have run into the fact that Linux only resizes "from the end", not the beginning. You now can move the partition to the beginning (it will not be resized in this operation) and then add to its size using the vacated space "at the end" once it is moved. Where your copying idea may run into problems is that the new partition will be given a new device name (currently, your Ubuntu is on /dev/sda2), which will require your editing the fstab file to reflect its new location. It is doable, and there are a number of threads around which discuss it. If you have all your data backed up externally, I'd recommend doing a comple clean install, with the installation disk taking care of formatting, etc., after choosing the use entire disk option. My two cents.

---

