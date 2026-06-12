---
title: "dual boot windows 10/ ubuntu studio 14.04"
date: 2015-09-06
forum: New to Ubuntu
---

### Post by sc3sc3 on 2015-09-06
Hi,

I have a laptop with Windows 10 installed and
I just installed Ubuntu Studio 14.04 on another partition.

When booting the laptop I don't get an option to boot into Ubuntu,
Windows 10 is booted immediately.

What are the procedures to get a dual boot options ?

Attached I have the fdisk output
and the result of bootinfoscript.

Thanks for any help
Regards
sc3

---

### Post by sandyd on 2015-09-06
Have you checked the UEFI boot order? Ubuntu should boot before Windows.

Windows doesn't seem to show up in the GRUB boot menu at the moment, but we can fix that after we manage to boot into Ubuntu.

---

### Post by yancek on 2015-09-06
You have two EFI partitions.  The one on the first drive with windows only has an entry for windows.  You have another EFI partition which only contains Ubuntu efi files.  Have you tried setting the Ubuntu drive to first boot priority to see if it boots.  I don't use UEFI so I'm not sure how you would correct this, usually there is only one EFI partition but maybe you can have more than one.  Since the efi files for Ubuntu and windows are on different drives, I can see how booting would be a problem.

---

### Post by Aidan_Owen on 2015-09-06
Set Ubuntu to boot in your BIOS, then restart your computer. It should come up with a GRUB screen with an option to boot into Ubuntu or Windows Boot Manager.

---

### Post by sc3sc3 on 2015-09-07
Hi, thanks for the answer.
I realize now I installed the OSs on different disks.

When going to the Boot Option Menu( <F9> - through Windows 10), I get the following boot options:
- OS Boot manager
- Ubuntu
- boot from EFI file

From here I can boot into Ubuntu, but I cannot change the boot sequence.

In BIOS ( <F10> ) I can move "OS Boot manager" up and down in boot sequence, I don't see anything relating to the Ubuntu disk.

Thanks

---

### Post by Aidan_Owen on 2015-09-07
In my BIOS I have to push the + button on the keyboard to change boot priority.

---

### Post by sc3sc3 on 2015-09-07
I tried, I can't change the boot priority in Boot Option menu.

But I found this
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)

I'll read about it some more since it apparently might go wrong.

---

### Post by sc3sc3 on 2015-09-08
I did change the boot order with efibootmgr
and something went wrong.
Laptop didn't boot anymore, the partition with Windows got damaged so I had to do a restore of the Windows partition.

So I'll stick with <ESC> and <F9> when booting laptop.

I would ditch Windows altogether and do a clean single-boot install
but now I'm not sure if bios would allow to boot without a Windows partition.

I have a "hp envy dv7 7370eb", anybody any experience with a single boot Ubuntu install on this laptop ?

Thanks

---

### Post by oldfred on 2015-09-08
Every HP we have seen has needed a work around.
HP among others, modifies UEFI to also use description in boot and only allowed description is "Windows". That is not per UEFI spec, but perhaps a Microsoft suggestion???

But there are multiple work arounds. Some are better depending on whether dual boot,  only Ubuntu, or if you want a gui boot manager. UEFI has a fallback boot of just the hard drive entry (/EFI/Boot/bootx64.efi). That file probably is just another copy of the Windows efi file, but can be the grub or shim efi files. Then booting a hard drive entry boots Ubuntu/grub. 

Back up entire ESP - efi system partition and copy to another device. Is not large so should be easy to copy.

Detailed instructions for copying files also in link in my signature.
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
      
 HP Envy 700-430QE desktop used bcdedit to dual boot
[http://ubuntuforums.org/showthread.php?t=2260681](http://ubuntuforums.org/showthread.php?t=2260681)
Boot Ubuntu 14.04 LTS 64-bits on external hdd - HP Envy 17 w/Windows 8.1 Details
[http://ubuntuforums.org/showthread.php?t=2256244](http://ubuntuforums.org/showthread.php?t=2256244)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)

---

### Post by sc3sc3 on 2015-09-08
Thanks for the suggestions but I'm done tinkering.

I stay with the ESC/F9 option.

I'm also done with HP, won't buy a product from them anymore.

---

