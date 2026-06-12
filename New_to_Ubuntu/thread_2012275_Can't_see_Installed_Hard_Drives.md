---
title: "Can't see Installed Hard Drives"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by safir on 2012-06-28
I am a newbie to Ubuntu operating system. I installed Ubuntu 12.04LTS 64 bit on my computer that has two hard drives installed in it.  Checking the BIOS shows that both HDDs are present in the computer. One HD is 500 Gb while the other is 2 Tb. Opertaing system is installed on 500 Gb HDD. But under the Home Folder, it does not show the presence of two drives. By right clicking the Desktop icon and then clicking on properties, it shows that the Volume is unknown and the free space on the drive. Judging by the amount of free space, it would appear to be the 500 Gb HDD. But no where I can see the larger drive. When I try to use " save as"  to save a file, it only gives the option to store in Documents, Downloads etc in the Home Folder. I would like to use the larger drive to store pictures and music etc. How can I do it when I can't even see the large drive in the computer. Is there any way to accomplish this?  I tried running gconf-editor from ALT+F2 run dialogue but nothing happened and editor did not run. Any help in this respect will be highly appreciated. Thanks.

---

### Post by IWantFroyo on 2012-06-28
This would not be in /home.

Can you see it in /media?

---

### Post by oldfred on 2012-06-29
Nautilus will not show a drive but will show partitions. So is 2TB drive partitioned & formated? 

Post this from terminal

```
sudo fdisk -lu
```In Nautilus if you have not labeled partitions with names you know it just shows as a 200GB or similar size entry.

Also post this:
```
sudo blkid -c /dev/null -o list
```

---

### Post by Hendra Fuhrer on 2012-06-29
activate the EFI feature on your BIOS

---

### Post by mapes12 on 2012-06-29
Sounds like the 2TB drive either has no partition on it or is formatted with a file system that Ubu can't recognise. There is an application called GParted. If you run it you will see the 2TB drive in a GUI. It will probably locate your 500GB first but there is a toggle drop down (I think it's near the top right) where you can change the drive selection. From there you can select the drive then carry your required maintenance. Usually, Ubu drives are formated as ext4 these days.

You may need to reboot. Then go to Places>Computer and you should then see the drive. Double clicking it will mount it but I don't think you need to mount it when just saving files as this will mount it automatically.

I'm not on my Ubu box at the moment so posting from memory.

---

