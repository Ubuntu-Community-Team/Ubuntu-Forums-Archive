---
title: "[SOLVED] Windows XP on SATA Drive without floppy"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by subaruwrc01 on 2008-06-15
I'm wanting to dual boot with Windows XP and Ubuntu.  What I want to do first is install Windows XP.  However, that is where I run into problems.  I have a SATA drive that the installation doesn't recognize.  I've searched the internet, but nothing was directed towards linux.  I can't do the floppy route as I don't have one, and any of the program routes don't run in Wine.

Thanks!
Ryan

---

### Post by shifty_powers on 2008-06-15
hold on. you want to install windows first onto a blank hard drive, yes? so this computer does not have any os currently installed yes?

and how old is the computer? some old ones need to have sata drivers loaded onto a floppy, but any recent, i.e. last 3 years or so, will handle the sata at chipset level and will not be a problem. not perosnally come across that in a long time...

---

### Post by subaruwrc01 on 2008-06-15
> **shifty_powers said:**
> hold on. you want to install windows first onto a blank hard drive, yes? so this computer does not have any os currently installed yes?

and how old is the computer? some old ones need to have sata drivers loaded onto a floppy, but any recent, i.e. last 3 years or so, will handle the sata at chipset level and will not be a problem. not perosnally come across that in a long time...

I'm trying to do this on my laptop I am on now.  Ubuntu is installed.

The SATA disk is new, however Seagate doesn't offer the drivers for it on their site.

---

### Post by shifty_powers on 2008-06-15
silly question, but have you initialised the sata disk, seeing as it is new?

---

### Post by subaruwrc01 on 2008-06-15
> **shifty_powers said:**
> silly question, but have you initialised the sata disk, seeing as it is new?

Initialised how exactly?

---

### Post by shifty_powers on 2008-06-15
you need to install gparted and then do the initial format of the disk....

```
sudo apt-get install gparted
```

---

### Post by shifty_powers on 2008-06-15
so hangon, is the sata drive going to be an external disk then?

---

### Post by subaruwrc01 on 2008-06-15
I'm wanting to install it on my SATA drive in my laptop which already has Ubuntu installed.

I can't go the floppy route since Seagate doesn't make drivers for my hard disk.

I can't go the nLite route since it doesn't run on wine.

---

### Post by subaruwrc01 on 2008-06-16
Bump

---

### Post by lazyart on 2008-06-16
The floppy drive thing is not a linux issue-- Windows will only look for a floppy.  Seagate wouldn't make a driver for this. It's a chipset thing and the maker of your notebook would provide that.

You do realize that installing Windows after Ubuntu will trash grub, correct?

Usually the easiest way around the floppy disk issue is to go into your system setup and change the SATA controller to masquerade as an IDE by setting it to some sort of emulation mode.  This might also make it tough to get into whatever OS is already installed on the drive...

---

### Post by dark_harmonics on 2008-06-16
You need to find the drivers for your sata hardware if you want to install xp. There is no way around that. 

Did you check with your laptop manufacturer? They should have XP support in the way of drivers. You are going to need a usb floppy (i keep an ancient one around for things like this and old-style bios flashes) or you are going to have to slipstream the drivers into XP (which is pretty complicated just to do one install). 

Here is the order of what you have to do:
Download drivers and install into the floppy disk.
Set bios to its sata native mode off or compatibility.
Install XP on the drive
Configure XP to point the controller at the hardware (you have to force it).
On reboot change bios back to sata native mode on.

I dont have much experience with dual booting and so i have no idea how this will effect your dual boot. Hope any of that helps.

---

### Post by bumanie on 2008-06-16
I'm a little lost with all the above, but if you install the new drive in the laptop, then > sudo apt-get install gparted from ubuntu. Go to System --> Administration --> partition editor. You should see the new hard drive as 'unallocated'. Format by right clicking on the unallocated drive and choosing a filesystem type to format it to. Hope that is what you are after.

---

### Post by subaruwrc01 on 2008-06-16
> **lazyart said:**
> The floppy drive thing is not a linux issue-- Windows will only look for a floppy.  Seagate wouldn't make a driver for this. It's a chipset thing and the maker of your notebook would provide that.

You do realize that installing Windows after Ubuntu will trash grub, correct?

Usually the easiest way around the floppy disk issue is to go into your system setup and change the SATA controller to masquerade as an IDE by setting it to some sort of emulation mode.  This might also make it tough to get into whatever OS is already installed on the drive...

Yes, I know the floppy drive isn't a Linux issue.  Lenovo decides to royally screw people over these days and not provide anything important, so I can't get it from them.

I'm trying to do a fresh install of XP over the whole hard disk.

How do I masquerade it as an IDE?

---

### Post by subaruwrc01 on 2008-06-16
Here is all the downloads provided by Lenovo for my laptop.
Which one of these is the correct one to download and boot for the SATA drive?

[http://www-307.ibm.com/pc/support/site.wss/product.do?template=/product.do?template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&sitestyle=lenovo&brandind=10&familyind=370153&machineind=376166&modelind=385578&partnumberind=0&subcategoryind=0&doctypeind=9&doccategoryind=0&operatingsystemind=53385&validate=true](http://www-307.ibm.com/pc/support/site.wss/product.do?template=/product.do?template=%2Fproductpage%2Flandingpages%2FproductPageLandingPage.vm&sitestyle=lenovo&brandind=10&familyind=370153&machineind=376166&modelind=385578&partnumberind=0&subcategoryind=0&doctypeind=9&doccategoryind=0&operatingsystemind=53385&validate=true)

---

### Post by LeftyMills on 2008-06-16
I recently purchased a new computer with a SATA CD/DVD burner, a ASUS P5VD2-VMSE motherboard and a Hitachi SATA harddrive - no operating system. I would install XP and Ubuntu by myself.  I told the salesman/technician that I was concerned about the CD/DVD burner - how can I load the drivers without a floppy? He agreed, took out the SATA CD/DVD and put in the old type.
Then my problems began -
I could not get a gparted CD to work.  Usually I use the gparted that comes on the live Puppy Linux CD, but I got the TTY error.   Eventually I found that the gparted CD 3.4.9 (around Oct/ 07) worked if I did a force VESA.  Also, the live CD of Fedora 8 live of Nov/07 worked and has gparted built-in.
I tried to install Ubuntu 8.04 desktop but got graphic problems - diagonal coloured waves.  I then pressed F4 and tried to install in safe graphics mode - the installation worked beautifully.
Later I found that the experimental Puppy with the 2.6.25 kernel also worked on my computer.

---

### Post by subaruwrc01 on 2008-06-16
Ok, I figured out how to install XP on a SATA without slipstreaming or loading the drivers on a floppy.  Now to just set XP up to my liking.

---

