---
title: "Remove Minimal Grub"
date: 2017-10-06
forum: New to Ubuntu
---

### Post by brandoinorlando on 2017-10-06
Hi. I barely know anything about linux so i installed ubuntu the other day, i didnt like it for plenty of reasons so i decided to go back into windows 10 and attempt to uninstall it but i didnt know how to... so I went to C:\ and looked around in the folders and somewhere i deleted a folder called Ubuntu. Now, when i turn on my pc it sends me to a minimal gurb menu. When i type "exit" in there, it sends me to the same thing again except its more high quality looking so I do the same thing and only then does it boot me into windows. How can i get rid of this menu? I have tried factory resetting windows already and I cannot boot into ubuntu. The ubuntu version was 16.04

---

### Post by oldfred on 2017-10-10
You change default boot in either BIOS or UEFI before you delete the partition with the older boot code.

Is system UEFI or BIOS? 

If BIOS you must reinstall the Windows BIOS boot loader to MBR.
       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

If UEFI, you only need to change default in UEFI to make Windows first in boot order.

If you want to totally houseclean Ubuntu you have to remove the UEFI entry in its NVRAM and the /EFI/ubuntu folder in the ESP. But that is not required to make Windows default boot.
See UEFI menu clean up section in link below in my signature.

---

### Post by brandoinorlando on 2017-11-04
I have already tried changing boot order a while ago to set windows first and ubuntu last, also disabling ubuntu from the boot order. It keeps reverting against me.

---

### Post by oldfred on 2017-11-04
May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

But Boot-Repair cannot fix most Windows issues, you may need your Windows repair/recovery disk.

---

### Post by RobGoss on 2017-11-04
What does your machine do when you boot it up? 

Did you already delete the Ubuntu partition?

If you did in fact delete the Ubuntu partition, you will need to fix your Windows Master boot loader in order to boot into Windows again. Removing Ubuntu also removed the Ubuntu Grub loader and Windows will not boot up

---

### Post by brandoinorlando on 2017-11-06
When i boot it up it gives me a minimal grub 2 thing.
I type exit in there, and it gives me the same thing again but its more 1080p like instead of right in my face. I type exit again and the machine boots up windows 10 normally from there.
This error started when i wanted to somehow uninstall ubuntu cause i didnt like it so i tried to find out how to myself and went somewhere in my hard drive and deleted a folder called Ubuntu or something.

---

