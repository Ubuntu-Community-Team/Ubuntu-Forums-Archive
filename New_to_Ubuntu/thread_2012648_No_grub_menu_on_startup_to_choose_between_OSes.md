---
title: "No grub menu on startup to choose between OSes"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by Mousiekins on 2012-06-29
I'm dual booting Ubuntu 12.04 and Windows 7, and followed this guide from lifehacker: [http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

I set up partitions in Ubuntu (live boot), installed Win7, inserted boot drive for Ubuntu again, and installed Ubuntu.  When prompted, I rebooted... and Windows 7 opened, without any prompting from grub.

Is there any way for me to force the system to boot into Ubuntu so I can set up Grub properly? I've tried accessing it from a live boot, and while I can access and alter the files, there seems to be no grub-update to run.  I have also tried reinstalling Ubuntu, in case there was a step that I forgot.

Rescatux and SuperGrubDisk (I think I spelled those right; I'm at work, so my bookmarks aren't available right now) didn't change anything.

My next plan of action (pending suggestions) is:
1. Try to use bcdedit in windows
2. Try booting with boot-repair-disk

This is my first homebrew system and my first time setting up OSes on my own, so pardon my noobishness, and thanks for any advice :)

---

### Post by oldfred on 2012-06-29
Welcome to the forums.

While the lifehacker site is generally ok, it is now dated and without reviewing details all over, It may need an update to two to be correct now.  Grub2 is the standard now.

Best gui way.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

And if that does not correctly repair your system, run the Bootinfo report and post the link it creates.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
(was this thread) [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by Mousiekins on 2012-06-29
Thanks, oldfred!  That boot repair tool is what I have prepared for tonight, and if that doesn't work, I'll check out the other repair links.

---

### Post by wilee-nilee on 2012-06-29
> **Mousiekins said:**
> Thanks, oldfred!  That boot repair tool is what I have prepared for tonight, and if that doesn't work, I'll check out the other repair links.

If the bootrepair does not work be sure to post the bootinfo summary's http address, that is really our best way to help you.

If you run other repairs after having the summary run it again to post it, so we have a accurate picture.

---

### Post by Mousiekins on 2012-06-29
I will do that... I may have to ask for help figuring out how to get the info, but I'll post here if so.

Meanwhile, a coworker has suggested that I set up my bios to boot in EFI, then switch it back, because grub can get it mixed up if I've never put the system in EFI...?  (I remember the steps better than the reason, in this case.  Easy to try if all else fails.)

Still an hour and a half before I can resume working on this machine.

---

### Post by Mousiekins on 2012-06-29
Boot repair fixed it!  Thanks so much!

---

