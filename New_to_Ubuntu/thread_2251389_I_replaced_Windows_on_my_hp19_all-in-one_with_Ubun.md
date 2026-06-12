---
title: "I replaced Windows on my hp19 all-in-one with Ubuntu. It won't boot properly"
date: 2014-11-04
forum: New to Ubuntu
---

### Post by vanceternowski on 2014-11-04
I went through the installation process from a flash drive, and everything was working fine. Ubuntu opened up without a problem. I restarted the computer, removed the flash drive, and was given an error message, saying there was no OS installed. I plugged the drive in again, restarted, and it brought me to my installation options again, so I hit install Ubuntu. The installer told me that Ubuntu 14.04 is already on the computer. 

I imagine this means that the problem is somewhere in the boot menu. I went into the BIOS and changed the boot order, but no dice. Turned off Secure Boot, and still nothing. Any recommendations would be helpful.

---

### Post by JKyleOKC on 2014-11-04
Will it still boot properly, after your repair attempts, if you have the flash drive in place? If it does, your problem is probably that the default installation process put part of the critical boot-loader program onto the flash drive rather than on the hard drive. This is a relatively common happening. If that's the case for you, it should still be able to keep running if you remove the flash drive once the boot stage completes.

My own tendency should I encounter such a situation would be to download the Boot-Repair package, install it on the hard drive, then remove the flash drive and run Boot Repair. The intent would be to let this package re-install the boot-loader code and put it on the hard drive where it belongs.

However I've not needed to do this, and it might not be a valid answer for your situation -- it might even make things worse. Therefore don't do it on the basis of this message. Hopefully OldFred, the resident expert on boot problems, will jump in with his own suggestions and they will be much more likely to work than are mine! I just wanted to let you know you aren't being totally ignored...

---

### Post by vanceternowski on 2014-11-04
Hi Jim,

Thanks for your reply. I'll play around with it a bit more today. It seems that, when I remove the flash drive, everything continues running just fine, but if I restart the computer, it tells me there's no OS. If I look a little deeper and go into the BIOS, I can see Ubuntu, so it's definitely on the hard drive. I think your suggestion about boot-repair is right on the money, but only time will tell.

---

### Post by JeQhdMD on 2014-11-04
If you run the gparted (or similar) program, you should see how the install is physically structured on your hdd.  Plus, you should see if the grub bootloader was on sda0 or sda1 (correct) OR if the bootloader was installed on sdb or sdc etc . . in other words, on removable media versus the hdd.  

I think Jkyle is on the right track re using boot repair . . . or another option is just to do a re-install (be sure to use the last option "something else" vs installing "alongside" any other OS.).   There is a place (read all the install screens carefully and completely  - - there is an option on the install screen re "where" the bootloader will be installed.

BTW, just in case the issue is different than it seems now, it's always best to provide the specs on your machine (ram, gpu type, and if the system is standard bios or uefi).   Also, you indicated you replaced windows - - so, any remnants of windows showing up when running gparted?

One additional note . . I've found it very helpful to have a Live OS (cd/dvd/flash-stick) running a version of Linux designed for system analysis and repair.  My personal favorites are:
>   Parted Magic (costs a small amount for download link (aprox $5.00) or
>  Knoppix
>  4M Linux

They allow for running the OS in RAM vs off the media (much faster) and don't auto-mount your drives so you can actually make changes if/as needed.

---

### Post by vanceternowski on 2014-11-04
Thanks for your advice. It didn't help, but it definitely opened some more doors.

My machine is a lame HP all-in-One, as I'm too broke for a real computer. It's got 4g of ram, an ATA something-or-other, and is UEFI. 

I looked at gparted, and it looked like the bootloader was right where it needed to be, and everything was on the hdd. No Windows remnants (shards?) 

Apologies for the lack of knowledge and insight. I'm disgustingly new to this whole thing.

---

### Post by yancek on 2014-11-04
Which version of windows did you replace?  Did you install Ubuntu in UEFI or MBR mode?  Probably running boot repair and just posting the output here would help someone to help you.

---

### Post by oldfred on 2014-11-04
HP UEFI based systems will not boot Ubuntu directly in UEFI mode. While UEFI is designed to allow multiple booting, HP and others (discount from MS?) modify the UEFI to only directly boot an entry that says Windows.

Those with HPs have done several work arounds. UEFI will still boot the hard drive so some rename the hard drive boot file bootx64.efi. You may not even have the /efi/Boot folder for that currently but can create it. Some use efibootmgr to rename the ubuntu entry to be "Windows" and then it boots (of course dual booters have issues with that). Some have renamed the Windows boot file bootmfgw.efi which you may not have either, but can create.

More details:
 [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

Some other HP
      
 It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)


 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

If you need specific details on one of the alternatives, post the link to the summary report from Boot-Repair.

---

### Post by vanceternowski on 2014-11-04
I replaced Windows 8, and I installed it in UEFI mode. Here's the thing: [http://paste.ubuntu.com/8826142](http://paste.ubuntu.com/8826142). Boot repair looked like it was doing what I needed it to do, but the problem persists. What I end up with, when I restart the computer with the USB stick plugged in, is a grub menu that says:

Try Ubuntu without installing
Install Ubuntu
OEM Install
Check disk.

When I restart without the USB stick, I get an error saying "No Operating System Detected" or something similar, and if I hit esc and check out my boot options, Ubuntu is there, but if I select it, it will do the same thing. It looks like Ubuntu's already in the computer, but I can't get it there without the USB, and anytime I restart, I'll lose all of my programs and files and whathaveyou.

---

### Post by yancek on 2014-11-04
What you indicate you see on booting in your last post means that you are still booting from the installation medium, your flash drive.  Your boot repair output shows you have an EFI partition with the Ubuntu files in it.  HP has apparently made some changes (see the post by oldfred above and the links) to its BIOS which cause problems.  You also installed using LVM so just wait for someone more familiar with it to respond.

---

