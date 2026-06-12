---
title: "can't boot after restore with PartImage"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by jesrani on 2008-05-20
I have Ubuntu 7.10 installed on a P3, 1.1GHz desktop and want to transfer it to P4, 2.8GHz computer. I attached my working Ubuntu disk to the new computer and booted with Parted Magic 2.0 CD. I partitioned the new disk with 3 partitions, for /root, /home and /swap. My new disk partitions show as hda1, hda5 and hda6 in GParted while the old partitions are hdd1, hdd5 and hdd3. I made an image of hdd1 to hda2 and then restored this image to hda1. I have not used the restore MBR option as I don't know how to use it. I made changes to my fstab file to load /hda1 as /. I removed the UUID from this. But when I reboot, nothing happens, the computer just hangs. I think this has something to do with GRUB, MBR but not sure what. Please help.

---

### Post by jesrani on 2008-05-20
Hello. I found the options to reload GRUB from the net and I used the commands as given. Now GRUB started but I got some error like "fsck.ext3: No such file or directory while trying to open /dev/hda5" and there was more. The system halted at root@ubuntu:~#.
I pressed CTRL+Alt+Del after few seconds and it went ahead till username screen. When I put my username and password, it says "your home directory is listed as /home/jesrani but it does not appear to exist. Do you want to log in with the /(root) as your home directory? It is unlikely that anything will work unless you use a failsafe session". So what do I do next. I think I need to edit my fstab but how and what values to put? How to point to my home partition?

---

### Post by drs305 on 2008-05-20
Please post your fstab and also the results of:
```
mount
```

If your fstab has UUID identifiers, also:
```
sudo blkid
```

---

### Post by jesrani on 2008-05-20
I went to the Session Option and loaded in Gnome terminal. Then I loaded GParted and checked the devices. Then I opened and changed fstab and now I can boot into the system with the new hardware. But it seems that the Graphic Card and Network card are not recognised correctly. I am getting only 2 resolution modes, highest and lowest. Also not getting network. When I opened SYSINFO, under Hardware -> Graphics and Hardware -> Motherboard, the subsystem shows unknown device. How to load the drivers.

---

