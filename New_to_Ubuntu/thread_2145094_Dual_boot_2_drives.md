---
title: "Dual boot 2 drives"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by wmchamp on 2013-05-14
I have a computer with 2 hard drives I wont windows on one and Ubuntu on other , web search I found (  [http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/](http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/)   ) trided this twice same both times I get a boot window but only one chose ubuntu. desk top has a folder with windows, when installing I used Gparted to make parttions on drive 0 I made 2 one 16 GB for windows rest as NTF stroage,on desktop I see drive 1 with windows files and 1 called storage .
New to linux have been researching using terminal ,but would need help . 
PS ran Boot repair ,still just ubuntu

---

### Post by verymadpip on 2013-05-14
Hi there.
If you are using Windows 8 I can't help you.
If you're using W7 or XP then it's a pretty straightforward process, unless UEFI comes into play, in which case, I can't help you :D.

Personally, I would install Windows to its own hard drive first.
Disconnect the Windows drive & connect the drive you wish to install Ubuntu to.
Install Ubuntu, ensuring the GRUB bootloader is installed on THIS drive.  That will be sd<some lettrer> (eg: sda).  Install the bootloader to the "whole drive" NOT A PARTITION (eg install to sda NOT sda1 or 2 or whatever).
Reconnect your Windows drive.
Change hard drive boot order in BIOS so the Ubuntu drive boots first.
In Ubuntu run sudo update-grub.
On reboot you should have a choice of operating system to boot.

THIS ISN'T GOING TO WORK FOR WIN 8 & UEFI WITHOUT SOME FIDDLING SO BE CAREFUL & WAIT FOR MORE HELP.

Good luck.

---

### Post by oldfred on 2013-05-14
From Boot-Repair run the BootInfo report and post the link it gives you. Then we can see details of where you are at.

---

### Post by wmchamp on 2013-05-14
Thank you verymadpip that worked 
Now how do I post to solved

---

### Post by verymadpip on 2013-05-15
Hi again.  Glad to have been able to help.
You can mark the thread as solved by using the "Thread Tools" just on the right above the first post on the page.

Welcome to the world of dual booting :D

---

