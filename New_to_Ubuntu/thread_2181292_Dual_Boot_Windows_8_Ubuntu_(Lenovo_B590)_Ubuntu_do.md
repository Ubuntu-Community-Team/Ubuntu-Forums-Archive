---
title: "Dual Boot Windows 8 Ubuntu (Lenovo B590): Ubuntu does not load"
date: 2013-10-17
forum: New to Ubuntu
---

### Post by federicodemaria on 2013-10-17
I've just bought a Lenovo B590 (Core i3 2348M; RAM 4BG; 500 GB hard disk; HD3000; 15.6"/W8) which supposedly is certified for Ubuntu. 
[http://www.ubuntu.com/certification/hardware/201208-11535/](http://www.ubuntu.com/certification/hardware/201208-11535/)

On the mentioned page I've downloaded and burnt on a CD the Ubuntu 12.04.2 LTS 64-bit. 

I've inserted the CD and turned on the computer, but Ubuntu did not load. 

Should I try with the 32-bit version? 
I don't really understand what the difference is. On the Ubuntu web page they say that "If you have a PC with the Windows 8 logo or UEFI firmware, choose the 64-bit download." I've found that somebody else had the same problem and apparently couldn't solve it. 
[http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-B590-3761-LG-hangs-on-boot-Linux-and-Windows7/td-p/1125451](http://forums.lenovo.com/t5/Linux-Discussion/Lenovo-B590-3761-LG-hangs-on-boot-Linux-and-Windows7/td-p/1125451)

I hope you can help me to solve this problem as I've been an happy Ubuntu user for years now, and I do not plan to go back to Windows. 

Thanks, 
f

---

### Post by fantab on 2013-10-17
You should go with Ubuntu 64bit... does this Lenovo come with preinstalled Windows?
How did you BURN your Ubuntu.iso to **[DVD]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows")** or [**USB**]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows")? Its important.

If it has Windows 8 then you may want to read [**THIS**]("http://ubuntuforums.org/showthread.php?t=2147295") first. It explains about UEFI dual booting.

Ubuntu will not load automatically, you have to choose BIOS/UEFI boot menu and choose CD/DVD/USB. Usually first boot device (default) is Hard Disk. It will be some key like F10, Esc or something else to reveal BIOS boot choice that you'll have to hit at boot.

---

### Post by federicodemaria on 2013-10-18
You are right, thank you. 
I've tried the CD I was first using and it was not working properly. I've then re-burned it on a DVD and first confirmed that it worked on another pc.
The problem I then had is that I could not access the BIOS (and still I can't) to change the boot menu. I've anyway found an options in the Startup Advanced Options of Windows 8 where I could tell the laptop to re-boot and start from CD. I'm now on Ubuntu (64-bit) and will try if it works, then install. 

Thanks a lot, 
f

---

### Post by mastablasta on 2013-10-18
you should check the lenovo manual on how to get into UEFI.

---

