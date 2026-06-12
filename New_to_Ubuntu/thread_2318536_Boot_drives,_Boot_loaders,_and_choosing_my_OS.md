---
title: "Boot drives, Boot loaders, and choosing my OS"
date: 2016-03-27
forum: New to Ubuntu
---

### Post by Cameron_Behning on 2016-03-27
Hey y'all!

First, I think every single one of you who help out on this forum are great! You must be quite a person to be willing to help out an idiot like me. 

So I was finally able to get a separate drive to put Ubuntu and it go me thinking about the booting process. What I would like to do is have something like I had on my old mac where every time I turn on the computer I get the option of which OS I boot into. I looked and looked through my BIOS/UEFI and could not find a setting to have that option by default. So in my research I think the solution is to use a bootloader, but I have no idea how to pick one or know even if this is right. Recommendations or solutions would be greatly appreciated. For your reference I have Windows 10 and Ubuntu 15.1 Thanks!

---

### Post by Bucky Ball on 2016-03-27
How are you choosing which OS to boot now?

Please let us know about your system. Are both OSs on the one drive, for instance?

---

### Post by grahammechanical on 2016-03-27
I am only familiar with BIOS boot systems not UEFI boot systems. When we have 2 or more drives a BIOS boot system will let us assign a drive to load an OS from. I assume that a UEFI boot system will give the user the same option.

It is usual for an Installation of Ubuntu to install a boot loader. The Linux boot loader (Grub) will detect the Windows operating system boot loader. And if we have set the BIOS/UEFI to boot from the drive where Grub has been installed then we should be getting a boot menu that will let us choose which OS to load.

Now, it gets complicated. With a UEFI boot system we can install an OS in EFI mode or BIOS/Legacy/CSM mode. If we only have one OS then it does not matter if it has been installed in EFI mode or Legacy mode. When the install mode does matter is when we install 2 or more OS. Then each OS must be installed in the same mode as the first OS.

Windows 10 when pre-installed will surely be installed in EFI mode. So, the question is this: Was Ubuntu 15.10 installed in EFI mode or legacy mode. I am guessing that Ubuntu was installed in legacy mode otherwise you would not be asking about the possibility of using a boot loader.

Regards.

---

### Post by yancek on 2016-03-27
You don't need to pick a bootloader as both windows and Ubuntu have bootloaders already with the system.  If they didn't, they would not boot.  If you have windows 10, you are probably using UEFI so read the link below.

  [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Are you using a Mac now?  If not, what hardware are you using?  Details please.

You might get the boot repair software from the link below and run it and post the output here as it will have a lot of detailed information which can be used to help.  Do NOT try to run and repairs.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Cameron_Behning on 2016-04-03
My current system is a windows 10 system intel i7. I have a total of 3 drives on my computer, a 51SSD with windows 10, a large 3tb drive just as additional storage and a smaller 120gb drive for Ubuntu.

As of right now, I have to hit my F10 key on start up to see a boot drive selector then select Ubuntu. Otherwise it defaults to windows 10. What I'm really looking for is a way to default get a boot drive selection at startup because the timing to hitting F10 and be tricky sometimes. Plus, that just feels like an unnecessary step.

---

### Post by Geoffrey_Arndt on 2016-04-04
So, it's unclear (at least to me) , , , , did you actually do the install yet (putting Ubuntu on the 120gb drive)???   If you did, and did it correctly, you will see a listing of OS's from which you can choose the OS (mine defaults to Ubuntu, but allows me to use down arrow to select Win7).

But if you haven't installed yet, and have a "Live" usb flash-stick (or DVD), then, that would indeed require you to activate the one-time boot key to select the external hosted OS and boot from it.

---

### Post by oldfred on 2016-04-04
It sounds like you are using UEFI as your boot manager.
And that would only be required if Windows is UEFI/gpt and Ubuntu is BIOS/MBR.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

What brand/model system and video card/chip or detail specs.

---

### Post by atrab101 on 2016-04-15
I hope you have been able to resolve your issue by now, but if not...

I am also a new user. I built an Ubuntu/WinXP dual boot system about two months ago.  I described this experience and good results in the Ubuntu Cafe.  I also have UEFI BIOS.   

 From the issue described, it sounds like F10 is pushed at boot at the right instant to bring up boot menu.  This is, I presume, the same as the F8 choice on my system which is a UEFI BIOS selection, rather than a separate boot loader.  This is what I have to do on my system, if I were to have my WinXP drive as the first priority hard drive in the UEFI BIOS.  On the other hand, if the Ubuntu drive is the first priority hard drive, then the system goes to the GRUB menu, which gives me about 10 seconds to choose which drive I wish to boot.  I believe this time can be adjusted.
 
 So presuming you have GRUB installed, you may be able to resolve the issue by insuring that the Ubuntu drive is the first priority in the UEFI BIOS.  On my system that choice is made in what is called the Advanced Mode (vs. EZ) on the Boot page.  The choice isn't visible until I scroll down.  Then I see Boot Option Priorities, then select Hard Drive BBS Priorities to further select the hard drive priority at boot.  I know that our systems are different, so all may not be the same.  Here's some info on my configuration as shown in my ASUS UEFI BIOS Utility:
 
 Motherboard: ASUS M5A97 R2.0
 BIOS version: 2603 x64
 Build Date: 6/26/2015
 Version (at bottom of EZ mode page) : Version 2.10.1208. Copyright American Megatrends, Inc.
 
 I am using Ubuntu 14.04.4 LTS
 My GRUB boot menu indicates: GNU GRUB version 2.02~beta2-9ubuntuv1.7

Regards 

Ubuntu Just Works :)

---

