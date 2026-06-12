---
title: "boot problem"
date: 2011-12-06
forum: New to Ubuntu
---

### Post by Arendyl on 2011-12-06
I recently filled up my computer harddrive to 100%, and now when I go to boot it, it won't load. After the initial ubuntu loading screen, it goes to the black and white loading page where all the programs are starting (I think). It loads about 15 programs before getting stuck at this: "Starting TiMidty++ ALSA midi emulation..." and nothing happens. Could this be because my computer is full? Your help is appreciated.

---

### Post by critin on 2011-12-06
Possibly/probably...I know that disks needs some room to work.  Sounds like its time to move pics/videos/etc to the backup storage and delete from the disk or get a bigger disk.

---

### Post by Gone fishing on 2011-12-07
Boot to a live CD move some of the files to external media see if that fixes the problem.

---

### Post by Arendyl on 2011-12-07
> **Gone fishing said:**
> Boot to a live CD move some of the files to external media see if that fixes the problem.

How do i go about doing that on a live disc? can i still access my files to delete them?

---

### Post by drs305 on 2011-12-07
Can you boot the recovery mode option from the Grub menu and get to a root prompt?

In the recovery mode you may have an option to make space "Try to make free space". 

If you can get to the root prompt but don't see that item in your recovery mode menu, you may be able to clear enough space to at least boot by running:
```
apt-get clean
```

---

### Post by Gone fishing on 2011-12-08
> can i still access my files to delete them?

Yes

---

### Post by illgetit on 2011-12-08
You might have to mount the harddisk when you boot with the live cd.
Assuming your only running 1 harddisk, it's more than likely named sda1.
If that's the case, just do this
 ```
mount -t /dev/sda1 *mountpoint*
```

---

### Post by Arendyl on 2011-12-08
@drs305
 
 Thank you, it worked perfectly. I don't exactly know how I pulled up the root prompt (Crtl + alt + --> i think), but i managed it. It now runs perfectly and I made a gigabyte of free space to avoid this problem again. Thanks for every ones help.

---

### Post by drs305 on 2011-12-09
:-) Glad it's working.

If you find yourself short on space again here is a guide that might help you in finding what's taking up the space:
[HOWTO: Recover Lost Disk Space]("http://ubuntuforums.org/showthread.php?t=1122670")

If you need to grow your Ubuntu partition:
[Expanding an Ubuntu System Partition]("http://ubuntuforums.org/showthread.php?t=1219270")

Happy Ubuntu-ing !

---

