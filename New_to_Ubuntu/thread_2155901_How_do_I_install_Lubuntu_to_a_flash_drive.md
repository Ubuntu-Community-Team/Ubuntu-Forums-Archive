---
title: "How do I install Lubuntu to a flash drive?"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by Predictability on 2013-06-19
I'm trying to find out how I can install Lubuntu onto a flashdrive so I can run linux on other computers, but I don't know how I can install it to the flashdrive.   I've tried unetbootin, but I think that's an installer.  I don't know much about partitioning.  Is there a way to do this, and make the flashdrive bootable (with folders like /home to save files)?

---

### Post by justynt on 2013-06-19
I know you can with LILI [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) Only with Ubuntu though, just give it some persistent memory. When you boot into live mode you can save changes onto the usb.

---

### Post by C.S.Cameron on 2013-06-19
Doing a Full install to flash drive is similar to installing to internal drive.
Following is step by step for installing 13.04 on a 8GB flash drive on an Intel machine.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue.

At "Installation type" select "Something else".
Continue

Confirm Device is correct.
Select "New Partition Table".
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "+".
Make "Size:" about 1000 MB.
Select "Primary".
Location for the new partition = "Beginning of this space".
"Use as:" = "FAT32 file system".
And Mount point = "/windows".
Select "OK"

Click "free space" and then "+".
Select "Size:" = 5000 to 7000 megabytes, "Primary", "Beginning of this space", Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "+".
Select "Size:" = 1000 to 4000 MB, "Primary", Beginning, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)
Click "free space" and then "+".
Select "Size:" = remaining space, (1000 to 2000 megabytes, or same size as RAM), "Primary", "Beginning of this space" and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, computer name, username, password and select if you want to log in automatically or require a password.
Requiring a password to log in and selecting "Encrypt my home folder" are good options if you are worried about loosing your USB drive.
Select Continue.

Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if, when partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You can revise grub later, if you wish.

---

### Post by Predictability on 2013-06-20
> **justynt said:**
> I know you can with LILI [http://www.linuxliveusb.com/](http://www.linuxliveusb.com/) Only with Ubuntu though, just give it some persistent memory. When you boot into live mode you can save changes onto the usb.

I have Kubuntu installed on my main laptop, this would be for other laptops I want to use linux on that only have windows.  Will LiLi run through WINE?

---

### Post by nerdtron on 2013-06-20
> **Predictability said:**
> I have Kubuntu installed on my main laptop, this would be for other laptops I want to use linux on that only have windows.  Will LiLi run through WINE?

Don't use LiLi if you are on Kubuntu.
Use the Startup Disk Creator. It's a GUI and very easy to use. Install it from the software center.
or from the command line ```
sudo apt-get install usb-creator-kde
```

---

### Post by Predictability on 2013-06-20
> **nerdtron said:**
> Don't use LiLi if you are on Kubuntu.
Use the Startup Disk Creator. It's a GUI and very easy to use. Install it from the software center.
or from the command line ```
sudo apt-get install usb-creator-kde
```

Ok, thanks.  I'm doing that now.  But I have the Lubuntu installer ISO, which comes with a live CD and an installer.  Is there a way I'd still be able to save files onto the flashdrive and keep them when I boot into it?

---

### Post by nerdtron on 2013-06-20
Yes indeed. When you are in the Startup Disk Creator Main interface, you'll see there on the lower part, the radio button "Stored in reserved extra space". I think the limit here is only 4GB because that is the limit of a FAT32 flash drive. (FAT32 is needed for you to "burn" the ISO to the USB drive)

If you need more space, I think you should do a "full install" as stated by C.S.Cameron.

---

### Post by Predictability on 2013-06-20
> **nerdtron said:**
> Yes indeed. When you are in the Startup Disk Creator Main interface, you'll see there on the lower part, the radio button "Stored in reserved extra space". I think the limit here is only 4GB because that is the limit of a FAT32 flash drive. (FAT32 is needed for you to "burn" the ISO to the USB drive)

If you need more space, I think you should do a "full install" as stated by C.S.Cameron.

Ok, thanks for the help!

---

### Post by C.S.Cameron on 2013-06-20
With Startup Disk Creator, you can get as much persistent space as you want by using Persistent partitions rather than a persistent file, (casper-rw).

---

### Post by sudodus on 2013-06-20
If you want stability, and want to keep it up to date with security updates and other updates, I recommend the installed system, described by *C.S.Cameron* a few posts ago.

If you have a 16 GB pendrive, you can also select the 'installed system' from [this link]("https://help.ubuntu.com/community/InstalledSystemFakePAE"). You simply expand a compressed image to the pendrive and have an installed system 'at once'.

[COLOR=#696969]Don't worry about the fake-PAE. It is a minimal piece of software that makes the system work also with Pentium M CPUs. It does no harm in other systems.[/COLOR]

---

### Post by Predictability on 2013-06-20
> **nerdtron said:**
> Yes indeed. When you are in the Startup Disk Creator Main interface, you'll see there on the lower part, the radio button "Stored in reserved extra space". I think the limit here is only 4GB because that is the limit of a FAT32 flash drive. (FAT32 is needed for you to "burn" the ISO to the USB drive)

If you need more space, I think you should do a "full install" as stated by C.S.Cameron.

Is there a way I can have the folder/file that saves things be encrypted?

---

### Post by sudodus on 2013-06-20
Yes, if you make a full installation and have encrypted home (a choice in Ubuntu during installation). But such a system will hijack and destroy the swap of the host computers unless you disable the cryptswap. (I have such a system and can describe the details, if you want to go that way.)

 I wouldn't rely on some fix with a live or persistent live system. Yes, you can encrypt single files or directories more or less automatically, but it is hard to make it really safe, to lock out a competitor or enemy. It is better to use a tested system.

Or you can have a separate encrypted USB drive only for data. And to have a live USB drive without persistence.

I have no experience of Truecrypt and such methods.

---

