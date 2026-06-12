---
title: "USB boot freezing while trying to install"
date: 2023-10-28
forum: New to Ubuntu
---

### Post by omen-izunia on 2023-10-28
Hey all, I'm struggling a bit here.

To start, I am brand new to Linux. My PC currently runs windows 11 and after having numerous issues, I decided to try installing Ubuntu. The installation process sounded pretty straightforward, but unfortunately I have not been able to see much of any of it. As soon as I open the UEFI menu and select "Try or install it Ubuntu" or the graphics friendly version, the splash screen for run for a few seconds, then promptly freeze. I've tried a few things I've seen suggested online to fix this. I've disabled fastboot, and tried the nomodeset method without success. I tried LinuxMint as well, with the same methods and had the same issues. I've tried completely uninstalling my graphics drivers and have completely flushed my secondary SSD (after doing backups, of course!)

[ATTACH=CONFIG]292973[/ATTACH][ATTACH=CONFIG]292974[/ATTACH]I'm attaching a photo of my PC specs if that helps anyone get an idea of what's going on.

If anyone needs more info, please let me know and I'll do my best to get it for you! Thank you for your time, I just really want to get this working. 

Additional info

I can take apart a PC and put it back together, but I'm not the most known when it comes to the coding parts.

My computer does not have a disk drive, so I've been following the on-site guides to boot the install from the USB. In addition, I've tried flashing different versions of Ubuntu, and reflashing the drive in case something's happening to corrupt the files.

---

### Post by yancek on 2023-10-28
Did you download the Ubuntu iso from the official Ubuntu site?  What is the exact name of the iso file?  Did you verify the download with a checksum after downloading it?  What software or method did you use to put the Ubuntu iso on the flash drive?  Do you have options for UEFI and Legacy boot in the BIOS firmware?  Are you using the UEFI option? Do you have another computer available on which to test the usb to see if it boots to eliminate the possibility the usb is bad or the Ubuntu iso was not properly written to the drive?  Before the freezing, do you see any messages on screen?

---

### Post by MAFoElffen on 2023-10-29
After verifying that you have a good image downloaded... Be aware of a few things.

The read/write speeds on USB Flash drives suck. It really matters, and shows up when you buy off-brand, cheap flash drives. Even if your computer only has USB2.0 ports, buy name-brand USB3.X Flash drives. They will work faster and are more dependable. Some things are just not worth it to save a few cents.

Second, if you already have tested the image... At the start of the boot process, press the <Down-Arrow> to look at the Boot Messages. You will see that it says it is going to do a file check to verify that all the files in the image are good. This takes a while to do (especially on a slow Flash Drive), and if they do not bring up that screen like that, they often mistakenly think that their computer is locked up, not doing anything, when it really is. If you want to skip that, when it first comes up, if you quickly press <Cntrl><C>, it will skip that process.

Third. With that boot message screen up, watch the boot messages for any kinds of errors. Especially if they are displayed in red. Report those to us if it stops at an error. That will help us to diagnose what might be going on, or at what stage of the boot process it is failing at.

---

