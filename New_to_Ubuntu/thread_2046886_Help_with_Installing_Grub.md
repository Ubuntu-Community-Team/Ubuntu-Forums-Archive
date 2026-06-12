---
title: "Help with Installing Grub"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by dktaylor on 2012-08-23
I have really screwed up.  I was working in fixing a second drive windows install so I could dual boot and somehow either deleted or made my linux boot non-functional.
I am running on a 9,04 live CD (all I have) but actually have 12.04 installed on the hard drive.
I have tried google searching this subject and have tried a few things, but they have all failed.
I am at a loss of what to do.  I have my life on the linux hard drive so cannot afford to lose it.
I have a 12.04 live cd on a thumb drive but for some reason I am unable to get it to boot (tried all USB slots).  Bios will recognize the thumb drive but will not boot from it.
So I am in a quandary.  And on top of it all, I am new to linux by about 2 weeks and have very limited skills as of yet.
Anyone up to the challenge?

---

### Post by NikTh on 2012-08-23
Hi , 
how created  the usb thumb ? With unetbootin ? If no then try it. 

1.Boot in windows 
2.Download unetbootin for windows --> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
3. Download .iso of 12.04.1 --> [http://cdimage.ubuntu.com/precise/daily-live/20120817.1/](http://cdimage.ubuntu.com/precise/daily-live/20120817.1/)
4. Format the thumb drive to Fat32 
5. Open unetbootin as administrator and burn the new iso 

When boot from usb thumb , select "Default" first choise. 

If boot ok , you can check this --> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to fix your grub. (2nd option)
Thanks

---

### Post by dktaylor on 2012-08-23
No that will not work either since I never did get my windows boot working.  I have nothing right now except this 9.04 live cd.

---

### Post by Bashing-om on 2012-08-23
dktaylor; 

 You need to come up with a 12.04 boot medium, as grub is different between the two. Where to you get to when you try to boot. There may be help yet on your current install.

       kindest regards <==BDQ

---

### Post by dktaylor on 2012-08-23
I get a message stating "missing OS."  I actually tried to find Grub but it doesn't even find stage 1.  I think the entire directory is gone.
I guess for now when I get to work tomorrow I will try and download 12.04 and burn it to a DVD and try that.  Don't know what else to do.

---

### Post by oldfred on 2012-08-23
Do you have access to another computer with Windows7. You can create a Windows repairCD or USB flash drive. That should get your Windows working so then you can download Ubuntu. I always suggest having a liveCD or repairCD/USB of the current version of every system you have installed.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

On my system USB flash drives do not boot as a USB device, but as a hard drive. So I have to select which hard drive to boot. I normally just use the one time boot key (f12 on my system but it varies) and choose the "hard" drive which is my flash drive.

---

### Post by dktaylor on 2012-08-23
I can access my windows 7 at work, but at the same time I can get 12.04 and make a dvd of that as well.
Probably will do both and see which one works first.

---

### Post by oldfred on 2012-08-23
With Windows it needs to be the same 32 or 64 bit version. But not necessarily the same level version as the repair CD are all the same within 64 or 32 bit.

---

