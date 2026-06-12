---
title: "Installed Ubuntu on Legacy Bios rather than Uefi on dual boot machine"
date: 2021-08-09
forum: New to Ubuntu
---

### Post by barry1978 on 2021-08-09
I installed Ubuntu without knowing the significance of selecting the correct Bios to run from.
 
So then I tried booting into the Ubuntu on the Legacy Bios but wasnt able to modify the bios config from there. 
Then i was thinking maybe I cannot modify it from within the current Ubuntu as it is a configured to Legacy Bios. 
 
Then I booted from Ubuntu on USB drive.
Installed  Boot-repair and ran it. 
It told me to create a Efi partition even though I already had one. 
I went ahead and created another Efi partition in case Ubuntu could not read the existing one for some reason. 
Still got same result. 

Here are the results of the Boot-Repair

[https://paste.ubuntu.com/p/ht2bfX3xSC/](https://paste.ubuntu.com/p/ht2bfX3xSC/)

Any ideas very welcome. 

thank you

---

### Post by tea for one on 2021-08-09
Before we go any further, can you confirm:-

You have a backup of your Windows data?
You have a Windows repair disk available?
Can you still boot into Windows?

The reason I ask is that the partitions are confusing and we need to try and get you back to the position before you tried to install Ubuntu.

Subsequently, we can re-install Ubuntu as a dual boot.

---

### Post by oldfred on 2021-08-09
It looks like Boot-Repair did not show its normal info on the partitions at the top of report.
Not sure if system issue, or if some change in Boot-Repair?

But you should only have one ESP per drive or device. Most UEFI want only one. Technically the standard does allow more than one.
You can have multiple FAT32 partitions. And once UEFI has booted into grub, grub can configfile or chain load into files on another FAT32 (or even other formats if grub files) partition that has boot files, but is not an ESP.

---

