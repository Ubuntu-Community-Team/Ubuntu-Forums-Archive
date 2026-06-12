---
title: "moving /boot label to dif partition"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by littletinman on 2008-06-10
I have three partitions. Ubuntu 64, 32, and another test ubuntu. I need to install XP for some progrms that won't run in wine. I need to delete the test partition but it has the "/boot" lebel in the partition editer. I'm guessing this means that i need to label a dif partition that so it can find the Grub list on a partition that will still exist. Anyone know a simple way to do this?

---

### Post by littletinman on 2008-06-11
did i explain this right? I really need help fast. My class starts on monday and i need to do some pre-class stuff before then. Anyone?

---

### Post by signseeker on 2008-06-11
In terms of moving the boot partition - just create a /boot directory on one of the other partitions - and then copy the data in your (old) /boot directory across to it. Once this is done, you should be able to just change your fstab to point to your new /boot.

Although, it's much much easier to have XP installed first. Apparently M$ doesnt like not having the first part of the hard drive.

Good luck. 

PS - there are lots of guide on installing windows after linux. Just google it.

---

### Post by littletinman on 2008-06-11
so how would i do this. there are already /boot things in each 3 partitions. do i just change the fstab to /boot in the partition editer?

---

### Post by signseeker on 2008-06-11
> **littletinman said:**
> so how would i do this. there are already /boot things in each 3 partitions. do i just change the fstab to /boot in the partition editer?

I thought you said /boot was in the partition you wanted to delete? 

Dont change your fstab just yet either.

---

### Post by littletinman on 2008-06-11
well when i go into the partition editer the /boot thing is on that. but when i go inot the file system there /boot folders in each partition.

---

### Post by littletinman on 2008-06-11
well i've done this before except now i have too many primary partitions. so i have to delete one. Yeah, and the test partition was the last one i installed so it has the /boot flag.

---

### Post by signseeker on 2008-06-11
> **littletinman said:**
> well i've done this before except now i have too many primary partitions. so i have to delete one. Yeah, and the test partition was the last one i installed so it has the /boot flag.

If this was the last one installed - theoretically it contains all the information necessary to keep your system running. So you would need to copy all the information in it to a /boot partition somewhere else - and then change your fstab accordingly. If everything still works after a reboot - then it means you should be able to safely delete the test partition.

I still think you should consider wiping ur disks and doing a complete reinstall starting with XP.

---

### Post by littletinman on 2008-06-11
no, i def not doing a whole new install. sorry. i just need the new partition. so i take everything from the test partitions /boot folder and put it in another partitions /boot folder? is that right?

---

### Post by meierfra. on 2008-06-13
Grub does not use  boot flags. So you can just deleted the test partition and install XP.  Since installing  XP will overwrite the MBR  you will have to reinstall Grub after you installed XP. 

Click on FixGrub in my signature for instruction on reinstalling Grub.

---

