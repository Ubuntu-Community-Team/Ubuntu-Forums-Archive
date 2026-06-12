---
title: "second hard rive troubles..after using Gparted..."
date: 2008-09-19
forum: New to Ubuntu
---

### Post by hvac3901 on 2008-09-19
Gparted has partitioned my drive (i think) and i formatted it with the mk command in terminal. But even though i can see it in my system menu, i cannot mount the volume, am i missing something?

Also the drive use to have (has?) ubuntu 7.10 on it, and it comes up as an option in just before the boot splash come up in a list of OS to choose from based on the drive. Shouldn't what Gparted and the terminal command did, put a stop to this option at start-up?

thanks in advance.

---

### Post by Titan8990 on 2008-09-19
What error are you getting when attempting to mount the drive?


> Shouldn't what Gparted and the terminal command did, put a stop to this option at start-up?

No, because Gparted deals with partitions. GRUB, the bootloader, is located in a special place on the HDD know as the MBR (Master Boot Record).

---

### Post by hvac3901 on 2008-09-19
> **Titan8990 said:**
> What error are you getting when attempting to mount the drive?

The GUI didnt give one, it just said "couldn't mount volume" I will mount form the terminal later yeah, and see what it gives as error?

---

### Post by bumanie on 2008-09-19
If the drive or partitions have been altered, you will most likely have to edit /etc/fstab to reflect the changes.

---

### Post by hvac3901 on 2008-09-19
while trying to drag a folder into the drive for storage, i was told that i do not have permission to make the file in the destination.

---

