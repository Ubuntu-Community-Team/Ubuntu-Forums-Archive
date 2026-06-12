---
title: "well im stumped...."
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Rockbo on 2008-09-30
A friend of mine gave me the idea to install ubuntu to a flash drive so i could have a portable private operating system. Well i did that and it works fine. the only problem is that now, i cant boot into windows unless i have the flash drive in the computer. it comes up with grub's error 21 message. is there any way to bypass grub to just boot directly into windows without having the flash drive in the computer? AND more importantly, will the flash drive work in other computers?


thanks to anyone who can help me....

---

### Post by blithen on 2008-09-30
Hm...I'm not sure about the booting into windows thing. It should work in other computers, don't you have another computer you can test it on?

---

### Post by wolfen69 on 2008-09-30
windows xp? if so, put the xp cd in and boot to it. choose recovery console. choose windows installation 1. then type ```
fixmbr
```hit enter and done.

---

### Post by lukjad on 2008-09-30
Well, if you keep it, you would have a really good security system. ;)

---

### Post by snowpine on 2008-09-30
+1 to wolfen's suggestion, and to elaborate on *why*, you need to be careful installing grub that you don't mess with your hard drive's MBR (master boot record). In your case, the Ubuntu installer thought that the flash drive was a 2nd hard drive in your computer. So the MBR is looking to boot using Grub on the missing 2nd hard drive.

I have a spare computer with no hard drive that I use specifically for messing around with live CDs/USBs. :)

---

### Post by sdowney717 on 2008-09-30
The problem I think is grub boot loader has installed to the hard drive.

the windows you just want to boot like linux was never there.

So, get a windows install CD, and boot from it. Get to recovery mode command prompt and type in 'fixmbr'

That will let windows boot.

Go into your bios and set it to boot from a flash drive ahead of the hard drive.

Now, you need to somehow fix the flash drive install of Ubuntu so it just boots without grub.
OR, perhaps it will just work anyway when you put in the flash drive and boot the PC,

---

### Post by bobnutfield on 2008-09-30
I have installed a number of distros to a USB drive and the key to avoiding this problem is to be sure that grub is installed to the USB drive.  Then (at least on most modern computers), selecting the option to boot from the USB port.  There are a number of tutorials for this, notibly google Pendrive Linux.

---

### Post by Rockbo on 2008-09-30
well i think i know what im doing now. only problem is, when i run the recovery console, it asks for an admin password. i dont have one. at all. and just pressing enter without entering one doesnt work either. how do i get past this?

---

### Post by Kellemora on 2008-09-30
Hi Rock

You'll have to forgive this old guy.  If a Flash Drive is the same thing as a USB STICK (I still call them SD cards if they plug into that slot instead).

I've done the same thing messing around here.

How I fixed it was to go ahead and put GRUB on the MBR again, then took off the info to boot to the STICK (or actually moved it down and let Doze be at the top), leaving only the DOZE in the grub bootloader.  After that it worked just fine, except rather than going directly into the Doze, you saw 3 seconds of the bootloader screen first.  In essence, the Doze was the default boot from Grub.  
Then if I did want to use the Stick, I could, but had to be quick on the gun to catch the bootloader before the Doze kicked in.

TTUL
Gary

---

### Post by Keen101 on 2008-09-30
You need to restore the MBR bootloader for windows on the machine while the USB drive is not plugged in.

I recommend the Super Grub Disk.

Then you also need to install the GRUB bootloader on your flash drive if you wan to boot it on any computer.

I've done this a couple of times. I have an external Ubuntu install which i'm typing from.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by NewDisciple on 2008-09-30
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

I have used this numerous times on other computers.  Needs older live cd version; like 7.04 or 7.10.  Current versions will not have ms-sys in the repository.

---

