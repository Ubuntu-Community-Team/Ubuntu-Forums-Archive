---
title: "&quot;mbr&quot; application in synaptic"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by rng on 2011-11-04
I notice an application called "mbr" in synaptic package manager. Could someone please tell me what exactly does it do. From its name and the brief description given, it will write master boot record. Can it be used for repairing windows hard disks and partitions?

---

### Post by illgetit on 2011-11-04
From what I've seen about the MBR package, I wouldn't rely on it.
If you're looking for help with your mbr, you might try [this]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by rng on 2011-11-05
Can this application ("mbr") installable from synaptic be used to repair windows mbr if we lose windows while installing ubuntu? I will appreciate if you would share your knowledge and experience with this appication.

---

### Post by drs305 on 2011-11-05
> **rng said:**
> Can this application ("mbr") installable from synaptic be used to repair windows mbr if we lose windows while installing ubuntu? I will appreciate if you would share your knowledge and experience with this appication.

It can. But it seems on the Ubuntu forums we've generally used 'lilo' to repair a broken Windows MBR. I used to issue the 'mbr' commands but some users indicated they had better success with 'lilo', so I switched and it has been very reliable.

What either 'mbr' or 'lilo' does is merely repoint the MBR directions to the partition with the boot flag. If the Windows boot files are intact and the boot flag correctly points to them, you should get the Windows bootloader menu.

For lilo, here are the commands we generally use. Change 'sda' if the Windows drive is different.
```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
When running the commands you will be told lilo is not fully configured and that you need to run more commands. To restore the Windows bootloader, this is not necessary and should NOT be accomplished.

---

### Post by rng on 2011-11-05
Thanks.

---

