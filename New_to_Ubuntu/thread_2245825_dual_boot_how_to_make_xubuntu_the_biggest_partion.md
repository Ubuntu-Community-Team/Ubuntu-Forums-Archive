---
title: "dual boot how to make xubuntu the biggest partion"
date: 2014-09-26
forum: New to Ubuntu
---

### Post by christoph5 on 2014-09-26
i have a new laptop with a new clean install of windows 7 now wich i want to keep, but i dont need it so big, its using about 40 gb now, i want the windows partiotion to be like 50 gb and the xubuntu to be like 250 gb, my total hd is about 300 gb

there is showing my hd is about 320 gb in xubuntu installation partition changing, and there is a Vista loader there wich is taking 10 gb, i tried to change that one and format it andchange to 250 and it give me error "can have a partition outside the disk" ????????

---

### Post by yancek on 2014-09-26
Boot the Xubuntu installation medium and run this command to post info on partitions:  sudo fdisk -l(Lower Case Letter L in the command)
You should be able to resize/shrink the windows partition to create free space on which to install Xubuntu with GParted but I don't think it is on the Xubuntu installation medium.  You could download it and burn the iso as an image to a CD, then boot the GParted CD and shrink the windows partition.  You will then have unallocated space on which to install Xubuntu.

I don't really understand your last sentence.  You can't make a 250GB partition out of a 10GB partition?  Windows 7 usually creates a boot partition but not 10GB in size.  Is this maybe a recovery partition?

---

### Post by christoph5 on 2014-09-26
can i use the simple option wich makes the both partions the same size, and edit it later inside xubuntu?

---

### Post by oldfred on 2014-09-26
Only resize Windows using Windows own disk tools and reboot immediately to have it run chkdsk and make repairs to its size. Also Windows NTFS partition really needs 30% free. One of the main reasons Windows gets slow is when partition is full and that is about 10% free. At 10% free a defrag can take forever as it just does not have enough working space.

You cannot use gparted on mounted partitions. So from your install you cannot use it on that drive, just other drives or flash drives. You can use live installer, if it does not have gparted you can add it or download gparted or parted magic live ISO and boot those which have gparted.

---

### Post by stalkingwolf on 2014-09-26
you may need to use gparted (should be on the live disk) , delete the vista partition then expand the win 7 partition into the unallocated area.

---

### Post by christoph5 on 2014-09-26
what happens if i just install xubuntu over the entire hardrive now, my laptop is a hp pavillion dv7 with windows 7 fully working with every driver
 have had problems before that after installing some linux over enite harddrivers and after wanna go back to windows XP it was back then, and i was totaly without drivers and everything lost, so the whole system was just basacly useless then, will the same thing happen now if i some day wanna reinstall windows 7 again? or is that only with windows XP?

---

### Post by Mark Phelps on 2014-09-26
> delete the vista partitionNot necessarily a good idea.

If you had Vista on this machine when you installed Win7, then Windows updated the Vista boot loader with the Win7 boot loader.  If you then remove the Vista partition, that erases the Win7 boot loader and you won't be able to boot Windows.

You can "fix" that by migrating the boot loader files from the Vista partition to the Win7 partition using EasyBCD.  I would do this and confirm that the PC then boots Windows from the Win7 partition BEFORE removing the Vista partition.

---

### Post by Vladlenin5000 on 2014-09-26
> **christoph5 said:**
> what happens if i just install xubuntu over the entire hardrive now, my laptop is a hp pavillion dv7 with windows 7 fully working with every driver
 have had problems before that after installing some linux over enite harddrivers and after wanna go back to windows XP it was back then, and i was totaly without drivers and everything lost, so the whole system was just basacly useless then, will the same thing happen now if i some day wanna reinstall windows 7 again? or is that only with windows XP?

Any OS you install may or may not come with all the necessary drivers. Any Windows user already knows that.

---

