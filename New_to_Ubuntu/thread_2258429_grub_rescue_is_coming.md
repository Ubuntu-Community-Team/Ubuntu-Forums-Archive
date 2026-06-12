---
title: "grub rescue is coming"
date: 2014-12-27
forum: New to Ubuntu
---

### Post by ankit12 on 2014-12-27
Hi,
I have newly bought freedos lenovo i5 laptop(500gb) and 1stly i installed the windows 8.1 and i partitioned into two drives "c"and "d" of 200gb and 150gb approximately and then i have done dual boot with ubuntu 14 (for that i gave 90gb out of 500gb ) ,the dual boot was working properly for 2 to 3 months then something happened and then when i "on" my laptop i got 
error: no such partition.
Entering rescue mode...
grub rescue>
So when i typed "ls" then i got
(hd0) (hd0,msdos4) (hd0,msdos2) (hd0,msdos1)
and i got "unknown filesystem" when i searched in 3 of that "msdosY" 
Idon't find "lost+found" in any of that 3 "msdosY" with any alternative modules.
WHAT TO DO?,AM STRUCK.
Even i kept live UBUNTU CD it was not burning (also 3rd party softwares,it wasn't burning) and same GRUB RESCUE window is coming ,i don't even have windows 8.1 CD 
PLEASE HELP
URGENT.

---

### Post by yancek on 2014-12-27
> then something happened 

If you don't know what the 'something' is, no one here will either.  Did you make any hardware/software changes just before this happened?  Are you able to boot any system?  If you still have the Ubuntu installation medium, boot that and go to the site below.  Get the boot repair software and install it or burn it to a CD and select the option to get a bootinfo summary to post here.  You haven't posted enough information for anybody to make a realistic suggestion.

---

### Post by ankit12 on 2014-12-27
Sir,
I kept ubuntu cd and when i did multi boot(function+f12)and selected cd drive then also am getting the same grub rescue window and i.e., am not able to boot the system.

---

### Post by yancek on 2014-12-27
If you are still getting the 'grub rescue' then it is trying to boot off the hard drive.  You need to get into the BIOS and make the change in boot priority.  You should see a message on screen immediately on booting the machine telling you which key to press to enter setup.  So you are not able to boot anything on the hard drive now?

---

### Post by ankit12 on 2014-12-29
sorry for late reply,Yes am not able to boot anything from my hard drive and if i change my boot priority to CD drive and kept Ubuntu booted CD in that, then also it is showing the "grub rescue" it means am unable to boot anything i.e.,hard disk or CD drive and if i go through non-booting method of grub rescue by typing commands 
So when i typed "ls" then i got
(hd0) (hd0,msdos4) (hd0,msdos2) (hd0,msdos1)
in the msdos4 or 2 or 1,i got "unknown filesystem" even if i typed the command (hdX,Y)/boot/grub/normal.mod or */usr/lib/grub/i386-pc* )
SO WHAT TO DO NOW..?

---

### Post by grahammechanical on 2014-12-29
The Ubuntu DVD does not use Grub. So, as previously pointed out if you are seeing "Grub rescue" then the machine is still looking to the hard disk for an operating system and it is finding the Grub boot loader. You need to change the machine's boot priority so that it first looks to the DVD drive for an operating system. In this way the live session will load. I have some questions,

Did you install Ubuntu inside Windows 8 by installing wubi.exe? Do you get a Grub boot menu? Do you get a boot menu (Grub) that lets you boot either Windows 8 bootloader or Ubuntu? Does Windows 8 load?

Regards.

---

### Post by ankit12 on 2014-12-29
Yes,i get a grub boot menu and in that we can select either windows or ubuntu (its dual boot) and thanks to yancek and Grahammechanical for helping me i repaired it by using usb (booted usb) in that ubuntu is loaded and after that by giving internet to my system,then by terminal coding thanks once again,bye.

---

### Post by Jonathan Precise on 2014-12-29
[s]I think wubi.exe does not work in Windows 8, apart from it not being supported anymore.

From my understanding, you (the OP) do not have an option to choose between Ubuntu and Windows 8, but instead Grub fails to recognize the Ubuntu partition (thus entering directly to Rescue mode, with the grub rescue> prompt). Is this correct?

Yes, as stated by grahammechanical, booting directly to the grub rescue> prompt, even with the Live DVD in, it seems that the boot priority in the BIOS settings is set to the HDD first, and CD/DVD second. Change the DVD to first and the HDD to second. You might get a bit more orientation on how to enter BIOS setup and change this setting in your BIOS manual.

Once you find the key to enter BIOS setup, you can upload a picture of you monitor screen if you still need help on how to change the setting.
After the setting has been changed, post back to see if it worked.

We also have a couple of more questions:

1) Before the problem begun, were you updating the system or installing a proprietary driver (e.g. Display driver, WiFi driver, etc.)?
2 a) If so, did the power go out, did the battery die, or did something else happen that made your computer shut down, sleep or not complete the update/driver installation?
2 b) If, and ONLY IF you were updating the system: What type of update was it? Was it the usual set of updates, or were you upgrading from 14.04 to 14.10
3) In ALL cases, right before the Rescue mode appeared, were you running 14.04 or 14.10?

Please answer the questions that apply to you, so we can better address your problem.[/s]

Sorry, should have refreshed before posting.

---

