---
title: "Grub 2 command line after hard reset"
date: 2020-09-19
forum: New to Ubuntu
---

### Post by Silver112358 on 2020-09-19
I don't have a lot of experience with linux, but am running an XPS13 9380 developer's edition, with Ubuntu pre-installed.

I should know better, but I hard re-booted the laptop after the display froze. Now it goes to a screen with a grub> prompt instead of booting into Ubuntu (or the grub menu). I am able to boot into Ubuntu with a live USB, and I ran the info summary from [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) which produced the output:
[http://paste.ubuntu.com/p/TyWFWMtPzK/](http://paste.ubuntu.com/p/TyWFWMtPzK/)

I also tried to figure out what commands at the grub> prompt might help, but I am sadly puzzled. Is there a way to recover my install, or is it irredeemably corrupted? I would lose some data if I wipe the drive and start over (not anything really dramatic though).

Any assistance is greatly appreciated!

---

### Post by oldfred on 2020-09-19
Your p3 is shown as unknown as if you forced shutdown and data was corrupted.

You can first try full fsck on p3. Run both commands as they have different parameters.

To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown to your partition(s) (I already changed to your p3)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p3
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/nvme0n1p3

---

### Post by Silver112358 on 2020-09-19
Yay, that fixed it! Thank you very much!

In hindsight, probably I should've figured it out without bugging anyone, but I was searching for boot and bios parameters instead of a linux check disk utility.

Thanks again!!!

---

