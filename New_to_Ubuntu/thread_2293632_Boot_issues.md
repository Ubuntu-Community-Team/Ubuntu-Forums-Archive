---
title: "Boot issues"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by Dana_Flaherty on 2015-09-06
Hi, guy...have had Lubuntu 14.04.03 on my old Toshiba laptop for over a year in a dual boot with the original XP, partitioned drive. After a recent update, Lubuntu won't launch.i get a lot of words, with a 'recursive error repaired, but reboot needed' message..but if I do reboot, nothing changs.. If I select XP to boot to first, then simply, 'restart',in XP,  it will boot back into Lubuntu as normal...I tried Boot Repair disk, no result. I tried the advanced options menu, but screwed something up, cuz when i select 'resume boot, the display is all 'stretched' to the left..Should i try to 
reinstall Lubuntu ?? Kinda like the OS...

---

### Post by yancek on 2015-09-06
The recent update on Lubuntu, did that include a kernel update?
Did the reboot fails on the first reboot?
Were you prompted to reboot after the update?
I don't understand your comment about xp.  It seems you are saying you can boot xp and when you shutdown xp and reboot you can boot Lubuntu?  Is that correct?
The boot repair software has an option to "Create Bootinfo Summary".  You didn't post a link to where you have uploaded it which you should do as instructed.  Generally best to use this option until you become more familiar with the Grub bootloader or bootloaders in general.

---

### Post by Dana_Flaherty on 2015-09-07
Thanx so much for the reply..
Don't know if it was a kernel update...i just do the auto update thing..i'm pretty sure i did the reboot after update, if it was asked for...
Yes, i can select xp from the 'grub' let it boot, then i get the old xp screen..i just then hit, turn off, select restart, then just let xp shut down, the 'grub' opens up, lubuntu is auto selected to auto start, and it does...No, i ddn't post the boot repair summary..where can i upload that to ??

---

### Post by sandyd on 2015-09-08
> **Dana_Flaherty said:**
> Thanx so much for the reply..
Don't know if it was a kernel update...i just do the auto update thing..i'm pretty sure i did the reboot after update, if it was asked for...
Yes, i can select xp from the 'grub' let it boot, then i get the old xp screen..i just then hit, turn off, select restart, then just let xp shut down, the 'grub' opens up, lubuntu is auto selected to auto start, and it does...No, i ddn't post the boot repair summary..where can i upload that to ??

Please follow the instructions here to generate a boot repair summary: [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
You will need to be connected to the internet while generating the summary for the link to be generated.

---

