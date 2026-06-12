---
title: "no boot disk has been detected"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by yeomansland on 2013-03-24
Hi, I created a installation disk on a usb. The installation looks fine. But when I remove usb and restart computer I get : ERROR : No boot disk has been detected or the disk had failed.

When I press F12 then I get : Please select boot device : UEFI : ST1000DM003-1CH162

If I leave the usb connected can choose to use it to reinstall or try it out.

That is what I've done to run boot-repair. 
 It discovered : "EFI" I followed all instructions until I received the permission to restart, with the message to 'make your bios boot on sda1/EFI/ubuntu/shimx64.efi file

--> I have no idea where to do this, because after pressing F12 I dont have any choice to choose what soever.

This is the url I had to copy after running boot-repair : [http://paste.ubuntu.com/5643135](http://paste.ubuntu.com/5643135)

I will this also send to boot.repair

I hope somebody can help me.

---

### Post by MoebusNet on 2013-03-24
I have no experience with uefi, but I did find this:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Maybe it will give you some idea what to do next. Hope it helps!

EDIT: the link above recommends posting in this forum (Installation & Upgrades):

[http://ubuntuforums.org/newthread.php?do=newthread&f=333](http://ubuntuforums.org/newthread.php?do=newthread&f=333)

---

### Post by yeomansland on 2013-03-25
Thanks for your reply.

But it doesn't apply here. I'm not trying to install ubuntu in windows
"if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not." is what I found on the page you mentioned.

If this post is on the wrong spot, because I'm really, really new to all this. First sorry for that, second can you tell me how to move it?

---

### Post by fantab on 2013-03-25
I see from your pastebin that you have only ubuntu. If that is true, then you don't need UEFI or EFI... [See Here]("https://help.ubuntu.com/community/UEFI"). So unless you want EFI for some reason, I'd suggest you ditch it. 

Also AFAIK you must have GPT partition table to uefi boot... but you have MBR. [Read Here]("https://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Disk_device_compatibility").

---

### Post by oldfred on 2013-03-25
Have you turned secure boot off? While grub's shim efi file has the Microsoft key, some computers will only boot the Windows efi boot file with secure boot on. Some even will not boot and then you do have to convert to BIOS mode.

But with secure boot off in UEFI/BIOS, and changing default to boot ubuntu, many UEFI system do boot Ubuntu. I would try that first. Also did you turn fast boot off in Windows or UEFI?

Only as a last resort Boot-Repair will convert a UEFI install to BIOS boot even on gpt partitioned drives. Ubuntu will boot BIOS mode from gpt drives but needs a small 1MB unformatted partition with the bios_grub flag. 
Also with very large drives, BIOS or grub seem to have a bug and may not boot a 1TB / (root) partition. Generally better to have a 25GB / (root) and use the rest of the drive as /home or data partition(s).

---

### Post by yeomansland on 2013-03-25
Thank you for all your help.

With all the information I've found here and there I managed (after 4 days and painful eyes ](*,)) to get the machine running.:lolflag:

I'm happy and gonna drink a glass of champagne. It was a bumpy road but I feel like reached destination for now. If you have any questions how to break a Packard bell, just ask me.

CU

---

### Post by yeomansland on 2013-03-25
Thank you oldfred, most of what you shared is what  I've been doing  the last few hours and it is working. At least the 12.04.2 version. That's it for today, maybe I'll try the 12.10 version later on.

---

### Post by BRAM2002 on 2013-03-25
Thanks! Your links are very useful for me :D   [[color=#EBECE4]_._[/color]](http://www.directory.bodybuildingtips-list.com/Business.html)

---

### Post by oldfred on 2013-03-25
Glad you got it working. :)

---

