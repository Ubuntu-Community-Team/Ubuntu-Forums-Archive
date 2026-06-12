---
title: "GRUB not appearing after new installation"
date: 2015-10-01
forum: New to Ubuntu
---

### Post by prosso on 2015-10-01
Hi, I'll try to explain the issue the best I can as I'm quite new with Ubuntu.

I've done a new installation of Ubuntu on a different hard drive partition, so I'm trying to get a Dual Boot menu but so far always is going strait to Windows 8. I can access the GRUB menu manually with the keyboard through the BIOS boot menu.

I've been reading a few posts about this, but I can have a clear idea of how to fix it. Here it is a bit of info of what I've done so far:

- 64 bit system and UEFI bios (I've seen this in the BIOS)
- I did run Boot Repair - Recommended Repair. These are the records: [URL="http://paste.ubuntu.com/12610154/"]http://paste.ubuntu.com/12610154/
[/URL]- Computer is a HP Notebook 15.

I have some problems with the touchpad mouse not working at all either, I'm still looking for a solution to fix it my self.

Thanks!

---

### Post by prosso on 2015-10-01
Forgot to specify that I have installed Ubuntu 14.04 LTS.

Thanks

---

### Post by oldfred on 2015-10-01
HP is not Linux friendly. They violate UEFI standard and use a description as part of UEFI boot. And of course only valid description is "Windows".
There are multiple work arounds depending on your configuration. Most copy grub & rename /EFI/Boot/bootx64. Some like a gui boot loader and add rEFInd.

More details, also in link in my signature.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Others with HP:

 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try different USB ports maybe  front.

---

### Post by prosso on 2015-10-03
Thanks Oldfred.

As I said, although I been trying now and then Ubuntu I'm not really that experienced with it; but I'll check all your info and get back with the output :) hopefully I'll with good news

Cheers.

---

### Post by prosso on 2015-10-08
Hi, 

Well, I'm glad to say that I have fixed the problem but I don't know how :) So, in order to get some knowledge from this I would like if any of you can have a look to the following Boot Repair records. These were my steps:

- After a few attempts of doing things without knowing what I was exactly doing, and getting confused with all the info I decided to delete the whole Ubuntu partition and do a fresh installation.
- Without running Boot Repair, and after doing all the 10 basic things after the installation, I followed the steps explained in this post [http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840) (post #6) but only til step 4 because I couldn't find any files like those in the directories. Result: Grub was appearing at booting up and Ubuntu running normally; the problem was that the option for windows wasn't working at all.
- So, I downloaded Boot Repair and run it to recover the backup files changed on the previous step. Windows was running fine again but Grub didn't appear (only manually via the BIOS menus)
- Then I was going to do the solution explained on this post [http://ubuntuforums.org/showthread.php?t=2133796]("http://ubuntuforums.org/showthread.php?t=2133796"). I run Boot Repair and the only difference from the previous attempt was that I unticked the Secure Boot. I rebooted the computer just to check that, this time, Boot Repair didn't work either. But it did! This is the report of it [http://paste.ubuntu.com/12679711/]("http://paste.ubuntu.com/12679711/") 

Now Grub starts normally, with Ubuntu and Windows working perfect (it also have a lot of different options to choose that I'm not sure what they are, but I'll find out).

Hope this info help someone else.

Cheers.

---

### Post by oldfred on 2015-10-08
HP puts all its system efi boot files into the ESP. Some vendors have a separate hidden partition with those similar files and somehow activate it.

But then Boot-Repair sees all the efi boot files and adds then to 25_custom as boot options. You may want to delete or edit 25_custom.

The fix of copying grub or shim into the Microsoft folder is what Boot-Repair used to originally do for those systems like HPs that do not boot anything but Windows. But any Windows update will overwrite the "Windows" file that is really grub and you have to copy the files again.
Most with HP copy /EFI/ubuntu to /EFI/boot and rename shimx64.efi to bootx64.efi. That is a hard drive default boot entry in UEFI. You may have to add that entry to UEFI boot options, but systems will let you use and set it as default. 

More details in link in my signature.

---

