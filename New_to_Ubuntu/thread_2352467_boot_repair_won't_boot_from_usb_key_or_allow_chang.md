---
title: "boot repair won't boot from usb key or allow changes from usb distro"
date: 2017-02-12
forum: New to Ubuntu
---

### Post by timberwolf007 on 2017-02-12
I've chased this rabbit all weekend and in frustration am probably missing something simple. I had a perfectly wonderful dual boot windows 10/ linux mint 17.3 (with most recent updates) system. I've got a few full installs of various linux distro's on usb keys. I have a 4TB hard drive that I wanted to put a couple of linux distros on permanently. In trying to install Arch on the 4TB harddrive I had trouble getting grub to install and in one attempt I'm sure that instead of typing /dev/sdb which is the 4TB hard drive, I type /dev/sda which is the harddrive in the laptop. Bang.A broken boot loader. I can get a grub prompt and I've chased various scenarios but to no avail until I came across boot repair.  I can stop the boot process and boot a usb distro but can't get the one on the hard drive to boot and windows won't even talk to me. The problem is that I used and ISO image writer to write boot repair to a usb key and it just won't boot. I then installed boot repair on the linux distro on a usb key but it doesn't want to repair grub on the main /dev/sda hard drive. When I try to change the place to repair (dev/sda) it wants to us the usb key that will not boot. As I've said, I'm probably missing something simple out of frustration and lack of knowledge. Any help will be appreciated. Thanks in advance.

---

### Post by oldfred on 2017-02-12
UEFI or BIOS on 4TB drive?
Do you have bios_grub for BIOS boot or ESP - efi system partition for UEFI boot?
I normally add both to all new or reformatted gpt drives.

 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by timberwolf007 on 2017-02-13
Sorry, you're right. That link is, [http://paste.ubuntu.com/23983815/](http://paste.ubuntu.com/23983815/). As to the question, the 4TB external hard drive was formatted gpt, with the first 921 GB given to windows for storage. Then I began installing Arch Linux after that. I don't know what form grub was trying to install as I got error messages and never got it completed. That's when I began working on the laptop. Am I going to be able to get the same boot menu that I had before? The one that LinuxMint 17.3 installed when I created the dual boot? I've tried so many different recommendations from so many sources that I'm not sure what I've got where as related to booting.

---

### Post by oldfred on 2017-02-13
I partition all new drives gpt, but do not have any really large ones.
I have also used gpt on all 16GB or larger flash drives.

And every drive gets both an ESP - efi system partition as first partition and bios_grub as second partition. Before I had UEFI, grub always used the bios_grub flagged partition for BIOS boot.
Now with UEFI, grub used the ESP for files & folders.
UEFI suggests that ESP be first partition on drive, but Windows often makes it second or third but not far into drive.

But installing in UEFI mode is a bit of a pistol. It requires manual copying & editing of several files from ESP on internal drive to external drive.
But BIOS boot is relatively easy, but with gpt you must have the bios_grub partition. Supposedly that can be anywhere on drive & grub will find it and use it with a BIOS boot install.

Either way with external drive you must use Something Else and choose grub2's boot loader install location to external drive.

This is a flash drive with a smaller ESP.
```
 Number  Start   End     Size    File system  Name       Flags
 1      1049kB  211MB   210MB   fat32        ESP        boot, esp
 2      211MB   213MB   2097kB               bios_grub 
```

Any install with Something Else which is required with  external drives or any second drive or any install with separate /home

 Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing) 

        Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)

---

### Post by timberwolf007 on 2017-02-14
I'll be sure to look at that suggestion about the external hard drive a little later. But as to the initial question, I've lost the ability to boot the dual boot laptop and don't know enough about grub to reinstall it the way it was ( or better). I wrote the boot repair ISO to a USB key with USB Creator in linux but it isn't even seen as a boot option when you pause the boot process to boot say, from the USB key or something else. Is the boot repair ISO like a live cd? Why won't it boot?

---

### Post by oldfred on 2017-02-14
I do not think Yann has updated Boot-Repair ISO since 14.04. 
Better to just use Ubuntu version live installer that matches your install and add Boot-Repair to it.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If UEFI system, you can create a UEFI only bootable flash drive. But must have UEFI set to boot in UEFI mode. But if flash is UEFI only, you will not boot in BIOS mode, which you do not want anyway.


 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by timberwolf007 on 2017-02-15
As far as booting UEFI or Legacy, this is where I may be getting into trouble. While not stupid of course, I'm horribly more ignorant of the boot subject than I need to be especially since I started with the goal to build my own Linux with the Linux From Scratch project. I originally had Windows ten on the laptop and to have a dual boot system then installed Linux Mint 17.3 and following the prompts disable UEFI and secure boot in the bios settings and enable Legacy. I followed the instructions on installing boot repair to the usb key and when run gave the error that it appears that I'm running in Legacy but I need to boot into UEFI and to switch it. When I changed the bios to diable Legacy and reinstate UEFI with the boot repair in the usb slot the screen says it can't find an operating system so it's not finding the boot repair usb key. The boot repair command dialog shows a separate /boot/efi partition on /sda1 which is the laptop hardrive where I want it to boot from (/sda4 specifically) but it also says the os to boot by default is the usb on /sdc1, the os now in use. I'm sure this is probably a simple fix but I'm just lost in the weeds. Is it that 7zip builds the UEFI drive and Legacy interferes with the boot? Why can't the UEFI enable bios not see the usb key? Thanks for all the work. I appreciate every reply and hope not only to get my system working but be able to help others and point them here to such an excellent resource.

---

### Post by oldfred on 2017-02-15
UEFI is now more complicated than the old BIOS as it is both the new UEFI and CSM/BIOS.
So more features & choices which you must sort thru.

You totally control how you boot from your boot menu in UEFI. But flash drive cannot change boot mode in UEFI.
From UEFI you should get two boot entries for a flash drive. One clearly UEFI:flash and one just flash which is BIOS boot. If flash drive configured for UEFI only then you only get that option.
But most UEFI require you to turn on Allow USB boot. My system required me to set to UEFI only for USB boot. Even the setting for UEFI or BIOS/CSM only would boot in BIOS mode, it should have offered both, but vendors UEFI is not always consistent/correct logically.

Lots of info on UEFI in link in my signature and many links to more info.

---

### Post by timberwolf007 on 2017-02-22
Thanks for all your help up to this point. I haven't given up but I also haven't solved the problem. You've been very informative and helpful and I appreciate it.

---

### Post by oldfred on 2017-02-22
Have you added both and ESP & bios_grub partition as first two partitions on drive?

---

### Post by timberwolf007 on 2017-02-26
I got the boot repair disk loaded onto a usb key and it booted the laptop and I used the recommended settings. When next I booted I got a black screen and a blinking cursor. I'm not giving up since I believe that I still have two viable os's (windows 10 and Linux Mint). I just need to fix the boot problem. As a last resort, when next I tried the boot repair usb, I had it purge and reinstall grub. Still the black screen. So I'm still working on the problem. Am I correct in believing that I have two os's that I just can't boot to? I haven't reformatted, reinstalled any os's, or resized partitions or done anything to the partitions except write grub files.

---

### Post by oldfred on 2017-02-27
Test post.

You show 11 posts & page 2, but forum is not going to page 2.

---

### Post by oldfred on 2017-02-27
Black screen is often another issue.
Do you get grub menu?
Or can you get grub menu by pressing Escape Key when booting if UEFI or holding shift key from UEFI/BIOS until grub menu appears.
If fast boot is on in UEFI, you may not have time to press any key.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]https://wiki.ubuntu.com/Kernel/KernelBootParameters

[/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

[URL="https://wiki.ubuntu.com/Kernel/KernelBootParameters"]
[/URL]

---

