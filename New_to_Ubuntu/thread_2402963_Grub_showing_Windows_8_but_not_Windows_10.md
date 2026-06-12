---
title: "Grub showing Windows 8 but not Windows 10"
date: 2018-10-06
forum: New to Ubuntu
---

### Post by yap211 on 2018-10-06
Hello, I just install ubuntu in my pendrive and I am able to start it. Also I have Windows 10 in my laptop.

However, when I enter grub, there is no selection of entering Windows 10, only have Windows Recovery Environment on /dev/sda2 and Windows 8 on /dev/sda4.
 Selecting these 2 options will lead to boot failure saying "Winodws failed to load because the system registry file is missing ,or corrupt".

I don't want to go to BIOS to swap the priority whenever I want to switch to another OS.

For your information, my computer originally boot Windows 8 but I had updated it into Windows 10. :confused:

I did try sudo update-grub but the outcome was just the same.

**My question is how to remove Windows 8 and add Windows 10 in grub.** Thank you.

[Update]
This is the pastebin I get from boot repair: [http://paste.ubuntu.com/p/J9kcJMRxYd/](http://paste.ubuntu.com/p/J9kcJMRxYd/)

---

### Post by ajgreeny on 2018-10-06
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by yap211 on 2018-10-07
pastebin link updated

---

### Post by yancek on 2018-10-07
You have Ubuntu installed Legacy/MBR and your windows is UEFI which are incompatible and the only likely way you can switch booting is to do so from the BIOS.  You need to convert Ubuntu to GPT which is explained at the Ubuntu documentation site at the link below and then re-install Grub from boot repair as suggested at the end of the output.  Or since this is a new install, just re-install Ubuntu UEFI.

ttps://help.ubuntu.com/community/UEFI

---

### Post by oldfred on 2018-10-07
Since Ubuntu on separate drive, I suggest partitioning (gpt) & formatting in advance & include an ESP on that drive. Or disconnect Windows drive so UEFI install will create both ESP - efi system partition & / (root) on gpt partitioned drive.

But then Ubuntu/grub will only see one Windows to boot. And Windows BCD has additional Windows entries.
Since only one Windows /EFI/Microsoft/Boot/bootmgr.efi.

System only really allows one ESP per device. But I believe I have seen Windows users create a second FAT32 partition, temporarily move boot flag making it the ESP and running Windows repairs from second Windows. Or maybe they just copied /EFI/Microsoft & edited BCD. Then move boot flag back to original ESP.
Grub may not care if you have two ESP, only UEFI. So grub may let you directly boot both Windows. You may have to experiment.

---

