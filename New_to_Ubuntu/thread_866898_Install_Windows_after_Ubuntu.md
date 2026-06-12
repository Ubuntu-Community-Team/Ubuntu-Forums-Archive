---
title: "Install Windows after Ubuntu"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by bjornie on 2008-07-22
Hello! I'm fairly new to Ubuntu, but already loving it. But I need to have a dual boot with Windows on my laptop. So far so good, I know how to reset Grub after the installation of Windows is complete, but - when I start the installation for Windows and try to create a new partition, Windows complains that I have to many partitions. My partitiontable looks like this:
/dev/sda1 - boot
/dev/sda2 - swap
/dev/sda3 - /

I have enough unallocated memory (about 30Gb I think). Shouldn't I be able to have at least 4 primary partitions?

If I delete my swap partition and swap on a file instead (the partitions all lay on the same drive - so I won't loose performance), can I somehow move the unallocated memory from the ex-swap partition to the rest of the unallocated memory at the end of the drive - and still have my Ubuntu-root partition intact?

Maybe it won't even matter if I swap on a file, to the Windows installation program?

Best regards,

---

### Post by Potatoj316 on 2008-07-22
You can only have 4 primary partitions.  You could put your swap in an extended partition (i dont now if having an extended partition counts in the 4) thats where mine was put by default.  I also dont think windows uses more than 1 partition.  I have 3 partitions, ext3-ubuntu, ntfs-windows, and swap(in extended partition).

---

### Post by hyper_ch on 2008-07-22
maybe you got a hidden partition? often you get that on new computers for recovery so they don't need to give you an install cd.

---

### Post by SunnyRabbiera on 2008-07-22
Perhaps its better if you back up your ubuntu stuff, get XP to hog up the drive (like it wants to) then come in and reinstall Ubuntu.
Your partitioning is the source of your problems here, sure its better for linux to use more then one partition but there is a limit on how many partitions a HD can take.

---

### Post by Troll_the_Great on 2008-07-22
+1 to the above post.You will have less headaches if you install Windows first and then on a separate partition install Ubuntu.
Cheers!

---

### Post by sailor2001 on 2008-07-22
If you install windows first, as suggested, right click "computer" "manage" "hard drives" and you can set your partitions from there for ubuntu install. "manual install or Largest free space.

---

### Post by fidamehran on 2008-07-22
Isn't there some way to regain the Linux bootloader if you run the live CD once again and boot into it? I forgot what it is, but I remember somebody saying something like that in some post I read one day.

---

### Post by oldos2er on 2008-07-22
There is: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by fidamehran on 2008-07-23
> **oldos2er said:**
> There is: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Yay !! Confirmed my point....

---

