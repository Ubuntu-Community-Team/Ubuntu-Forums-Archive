---
title: "Dual Boot Issue - Selecting Windows Boot Manager re-directs to GRUB"
date: 2019-04-08
forum: New to Ubuntu
---

### Post by ochoasrobots on 2019-04-08
I'm a Linux noob, and I just attempted a dual-boot on my HP Notebook 14-cf1015cl to install Ubuntu 18.04 alongside Windows 10. It appeared to work, except the computer would always automatically boot into Windows 10 (meaning I'd have to restart+hold shift to pull up Boot Options in order to boot into Ubuntu). Wanting the computer to instead boot into GRUB where I could choose between Ubuntu and Windows 10 when I powered on, I followed [mairabc's answer to this forum question]("https://askubuntu.com/questions/244261/how-do-i-get-my-hp-laptop-to-boot-into-grub-from-my-new-efi-file"). 

Now the computer automatically boots into GRUB, but when I select the "Windows Boot Manager" option, it just brings me right back to GRUB.

I have googled this issue quite a bit, but have so far been unsuccessful. I tried creating menuentries in the 40_custom and the 25_custom files under /etc/grub.d, I've tried using the Boot Repair tool, and I tried reinstalling Ubuntu.

Any help would be much appreciated! And let me know what additional information I can post to aid in the troubleshooting process.

---

### Post by yancek on 2019-04-08
The additional information you can post to get help is the output of the boot repair run with the Create BootInfo Summary option.  Post the link you get when it finishes here so members have access to that information.

---

### Post by Rubi1200 on 2019-04-09
Hi and welcome to the forums ochoasrobots :-)

As yancek mentioned, post the boot info summary here. Do not attempt any repairs until we have a chance to look at what is going on.

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Thanks.

---

### Post by oldfred on 2019-04-09
That fix was a very old fix where we copied grub to be the Windows boot file. We did that because some vendor had UEFI using description to boot and only valid description was "Windows Boot Manager".
But even for those systems, we now copy shimx64.efi to /EFI/Boot/bootx64.efi to boot a hard drive or fallback boot entry. Windows updates would always reset entry, so not a long term fix. And grub only boots working Windows or Windows that is not hibernated. And fast start up sets hibernation flag & Windows updates turn fast start up back on again breaking grub boot of Windows. So you have to use UEFI to directly boot Windows and turn fast start off again. Or having grub as "Windows Boot Manager" was only temporary and often caused more issues.

First undo the change, or move the bootmgfw.efi back to its original location, so you can boot Windows.

Then run Boot-Repair as suggested above, but do not run any autofix until someone has reviewed report.

---

