---
title: "How to fix an accidental Legacy mode install?"
date: 2016-01-05
forum: New to Ubuntu
---

### Post by giulio3 on 2016-01-05
Hello Forum users,
 

 [B]Problem:
 [/B]I switched my BIOS to Legacy mode on a pre-installed UEFI Windows 10 machine - accidentally. I can only install Ubuntu into legacy mode, and I am not able to switch back the BIOS settings.

 

 Windows has disappeared from the grub ( the boot options) and I can find no way of making it reappear.
 

 **Boot-repair report: **[http://paste2.org/k6scAjDC](http://paste2.org/k6scAjDC)
 

 **Goal (?): **I would like to switch my BIOS back to UEFI mode using Ubuntu.

 Ideally, I'd like to set up the dual boot system of my machine with both ubuntu and windows.**&#8203;**

 

 **Background info:**
 

 I am completely new to ubuntu, and tried to install on my new laptop:

 

 - Model: Lenovo z50
- RAM (size) : 6.7 GiB
- graphics card: AMD A10-7300 Radeon R6, 10 Compute Cores 4C+6Gx4
- OS type: 64-bit

 - OS: Ubuntu 14.04 LTS, installed from a USB stick.

 

 **What I tried to do:**
 1) I have tried boot-repair changing advanced settings.
 

 2) I tried to follow the code on this post [http://askubuntu.com/questions/509423/which-commands-to-convert-a-ubuntu-bios-install-to-efi-uefi-without-boot-repair](http://askubuntu.com/questions/509423/which-commands-to-convert-a-ubuntu-bios-install-to-efi-uefi-without-boot-repair). I changed the relevant number next to the sda, but I still wasn't able to change my BIOS to uefi, or see Windows again on my grub.
 

 2.1) I also tried to run the script suggest in this other post: [http://superuser.com/questions/376470/how-to-reinstall-grub2-efi](http://superuser.com/questions/376470/how-to-reinstall-grub2-efi) , but still to no avail.
 

 3) I uninstalled ubuntu, but I ended up in grub rescue mode. I tried this youtube-suggested script in the grub rescue mode:
 

 set boot=(hd0,msdos6)
set prefix=(hd0,msdos6)/boot/grub
insmod normal
normal
 

 but I got an error saying the partition did not exist.

 

 4) I couldn't manage to install rEFInd, and I don't really understand whether I should use it, or what it does.

 
**---------------------------------------------------**

  I would be extremely grateful for some help on how to fix this problem. I can just about copy and paste code into the Terminal...It is possible that I did something wrong in my previous attempts at solving the problem.

  

  The issue is explained as well as I understand, which is not very well unfortunately...so apologies if I haven't been clear enough!

  

  Much obliged.

---

### Post by ajgreeny on 2016-01-05
You don't change from UEFI to MBR/BIOS or vice-versa using an operating system, neither Windows nor Ubuntu; you have to enter the UEFI or BIOS setup when you power-on the computer by hitting a key, often Del or F2, but look for the first message you see, usually at the bottom of the screen, when powering on the machine.

Windows will never boot from a legacy BIOS setup if on GPT partitions, which I think it will definitely be using as it was pre-installed.

You state > I can only install Ubuntu into legacy mode, and I am not able to switch back the BIOS settings. but I am not sure why you say that; Ubuntu will install in UEFI mode without a problem, but you may have to jump a few hurdles with Win 10 to get it to work properly, such as turning off fast-startup and secure-boot.

For a start have a good long read through [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) which may give you lots of tips.  I am out of knowledge of Windows now not having used it since WinXP so there may be other posters who can answer with more details that I can.

---

### Post by giulio3 on 2016-01-05
Thanks ajgreeny.

My issue is that I cannot open the UEFI/BIOS setup since I installed ubuntu. Previously I accessed the UEFI/BIOS setup when Windows was still the only OS installed using a key specific to my machine (Novo button). Now, if I press this, I only get back to the grub, where I can see no way of accessing the UEFI/BIOS settings.

I have tried all other F* keys, Del: no joy.

Isn't there a way of changing the UEFI/BIOS setup from terminal? I'll keep reading the second link.

---

### Post by LostFarmer on 2016-01-05
lets verify just how the hdd is partitioned.  in a linux terminal run and post output :```
sudo parted -l
``` Note -l is a small L

ajgreeny-- is correct, the OS can not change that part of firmware settings, that I know of.  

If you put your live linux usb/dvd in , can you still press a KEY to select how  to boot , efi/legacy mode ?

---

### Post by giulio3 on 2016-01-06
LostFarmer, this is what I get:

g@g-Lenovo-Z50-75:~$ sudo parted -l
Model: ATA ST1000LM024 HN-M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot
 2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
 3      290MB   478GB   477GB   ntfs            Basic data partition          msftdata
 8      478GB   479GB   1000MB                                                bios_grub
 9      479GB   529GB   50.0GB  ext4
10      529GB   935GB   406GB   ext4
11      935GB   951GB   16.9GB  linux-swap(v1)
 4      951GB   978GB   26.8GB  ntfs            Basic data partition          msftdata
 5      978GB   979GB   1049MB  ntfs            Basic data partition          hidden, diag
 6      979GB   999GB   19.8GB  ntfs            Basic data partition          diag
 7      999GB   1000GB  1049MB  fat32           Basic data partition          hidden


 If I put the live linux usb I get to a screen like this one [http://i.imgur.com/zI1EUSt.jpg](http://i.imgur.com/zI1EUSt.jpg).
 I navigated the Help function, using Fn+F1, Fn+F3, Fn+...., and so on,  which is the closest thing I get to a "BIOS setup", but I can't see anywhere specifying legacy/UEFI, and don't really know any command to use after the boot: prompt.

---

### Post by westie457 on 2016-01-06
Do you get a Grub menu at Boot up or does the computer go straight to Ubuntu?

If you get a Grub menu do you have 'System Set up' near the bottom of the list?

System Set up will take you to the BIOS/UEFI settings page.

---

### Post by giulio3 on 2016-01-06
I get to a grub menu that looks like [this]("https://www.google.co.uk/search?q=grub+menu&source=lnms&tbm=isch&sa=X&ved=0ahUKEwi_2bfc_JTKAhWHow4KHY-hAMIQ_AUIBygB&biw=1167&bih=711#imgdii=wlGhhhubs_rKtM%3A%3BwlGhhhubs_rKtM%3A%3BOShP8qK23AQJaM%3A&imgrc=wlGhhhubs_rKtM%3A"):
*Ubuntu
Advanced Options for Ubuntu
Memory test (memtest 86+)
Memory test (memtest 86+....)
Windows Recovery Environment (loader) (on /sda7)
Windows Recovery Environment (loader) (on /sda3)

But there is no visible System Set up near the bottom of the list...sadly

---

### Post by ajgreeny on 2016-01-06
What do you get if you use the "Advanced options for Ubuntu"?

---

### Post by giulio3 on 2016-01-06
Just two other options for booting ubuntu: like [this]("http://www.howtogeek.com/wp-content/uploads/2014/09/640x480xboot-to-ubuntu-recovery-mode.png.pagespeed.gp+jp+jw+pj+js+rj+rp+rw+ri+cp+md.ic.erUGeLlYZO.png")...

Is there anything else I could try?

---

### Post by yancek on 2016-01-06
If you had windows 10 installed using UEFI, you must install other operating systems such as Ubuntu UEFI.  If for some reason, you could not get that to work, don't install Ubuntu until you find an explanation for the problem.  See the link below at the Ubuntu site for an explanation of UEFI dual booting.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Your problem is that you had windows 10 UEFI/GPT.  If you have GPT partitioning, then you must have windows installed using UEFI.  You have Grub code in the MBR of your drive and you also have a BIOS boot partition used with GPT when UEFI is not used.  You also have an EFI partition which contains both windows and Ubuntu files so you should have been able to boot both systems with UEFI.  The problem is having both an EFI partition and a BIOS boot partition with boot code in the MBR.  These conflict and you have seen the result.  You will need to find some way to access the BIOS and try the solution suggested at the bottom of the boot repair output.

> The current session is in Legacy mode. Please reboot the computer, and use this software in an EFI session. This will enable this feature. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode.

---

### Post by leunam12 on 2016-01-06
Go to google and search for the specific way to access BIOS setting for your particular computer and follow those instructions. Sometimes you have to be really fast since you only have a second or less to press the key. A cold restart may help you. unplug your computer and hold the power button for 45 seconds, then plug it back in and start it. You may see a menu message that did not appear before telling you how to go to BIOS

---

### Post by LostFarmer on 2016-01-06
giulio3--  with the comp off-  press the "Novo" button  , does it start and give you a small menu ?  If not , get help from lenovo if you still under warranty.

---

### Post by giulio3 on 2016-01-06
LostFarmer-- it worked! I managed to get back to the BIOS settings and change back to UEFI from Legacy.

Now, it boots only Windows, without going through the grub - but I guess that's because the ubuntu currently installed was in Legacy.
Now I should try to get back to ubuntu (any tips on how?), uninstall it and re-install it in UEFI mode, following the guides, right?

---

### Post by oldfred on 2016-01-06
Your Windows is still installed in UEFI mode, so you have to get into  UEFI to change boot. Or many systems have a one time boot key like f10  or f12. Or your novo button and other keys?

And many UEFI have a fast boot setting in UEFI. That assumes you have made no system setting changes or hardware changes & just reboots with all the settings the same. No scan of system for changes and then no time to press a key to get into UEFI or one time boot key.
Some systems will use a normal UEFI boot after full power down or cold boot not a warm reboot. If a laptop you also need to remove battery, hold power switch for 10 sec or so. Then when booting immediately press correct key to get into UEFI.
Some systems have a pin hole reset on bottom, some require jumping pins on motherboard to reset.

Some possibly similar Lenovo. Often UEFI very similar across models.
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

If you can boot into Boot-Repair from live installer, it can convert a BIOS install to UEFI install.
You show grub in MBR for BIOS boot, but that can remain without issue.
And you do show an ubuntu entry in ESP - efi system partition, but your fstab does not show the mounting of the efi partition, so not currently correctly configured for UEFI boot of Ubuntu.
Boot-Repair often adds the entry for UEFI access at bottom of grub menu.

But if you cannot get into UEFI, it will keep trying to boot the grub in the MBR in BIOS mode. You have to change boot to UEFI first.

---

