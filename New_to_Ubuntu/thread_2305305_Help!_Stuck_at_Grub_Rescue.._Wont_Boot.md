---
title: "Help! Stuck at Grub Rescue.. Wont Boot"
date: 2015-12-04
forum: New to Ubuntu
---

### Post by Beauchmin on 2015-12-04
I recently installed Linux Ubuntu aside Windows 10 and after having issues with the wireless settings, decided to get rid of Linux and just stick with Windows. I got lazy and just formatted the partition I had Ubuntu on then deleted the volume and extended the one I had Windows on (to combine them and give the HD space back to Windows). Now when I boot I'm stuck at the Grub Rescue screen and I cant boot from USB or DVD. Windows 10 is still installed on my PC though. I've tried accessing the BIOS by spamming f2, f5, f8, f11, and the escape buttons but haven't had any luck. 
I did research and some forums said I needed to change the boot priority in the BIOS to the USB and enter windows recovery to get rid of Grub with command prompt, but I can't get into the BIOS...
Some other posts said I need to find which partition Grub is in (which I tried in the picture) and set the root and prefix to boot, but haven't had luck with that either. Please help.
hd1 and hd2 are flashdrives with Windows 10 and Ubuntu installed on them

---

### Post by Beauchmin on 2015-12-04
I typed this up in Photoshop really fast on another computer. Hopefully it's easier to read, thanks. :)

---

### Post by oldfred on 2015-12-04
Do you have a Windows repair CD or flash drive. Or a Windows installer where you can get into the Windows repair console?

Better to use Ubuntu live installer in live mode and run this. If BIOS install it can add a Windows type boot loader to MBR. Do not think it can fix UEFI boot, but with UEFI you can just choose Windows in UEFI boot menu or one time boot key.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

      
 Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by Beauchmin on 2015-12-04
I'm unable to access the BIOS or boot from a flash drive or DVD. When I power on the PC it goes straight to Grub Rescue and I'm not given any other options. I've looked up the commands I can use in Grub Rescue and there's only about four (insmod, ls, set, and unset)

---

### Post by Beauchmin on 2015-12-04
Do you know of another way of entering the BIOS? I'm running an emachine and I've tried spamming f2, f5 f8, f11, f12, esc, and tab+delete right after powering on the computer.. It still sends me to Rescue Mode.

---

### Post by Vladlenin5000 on 2015-12-04
You need to press ESC _immediately_ after turning on.

---

### Post by oldfred on 2015-12-04
Many UEFI have a fast boot setting which is totally different than the fast start up in Windows.
What it does is speed boot by skipping all the normal hardware checks for new or different hardware or settings and assume everything is the same and immediately boot.

As Vladlenin5000 says you have to be quick.

Some will go thru a full system check after a cold boot or totally power down. Turn off system, iif laptop remove battery & hold power switch for 10 sec or so to drain all power. Then when system boots you have a very few seconds but more than before to press correct key. Best to know what key that is if not shown on screen as your system boots.

Some have had to open system, and remove motherboard battery. A few laptops have small reset hole at bottom of system. Best to download and review manual for your system to know details.

If you have a UEFI fast boot setting turn that off until system is totally reconfigured. My motherboard has fast boot settings for cold & warm reboot and a time delay setting to give a few extra seconds to press del or f2 which my system uses.

---

### Post by Beauchmin on 2015-12-05
When I spam escape while booting I get the screen I took a picture of for about half a second. It says "press DEL to enter startup" but nothing happens when I hit delete on that page. 
I added another picture that I thought might be important.. the prefix and root are set for the partition that I got rid of.. I tried downloading the grub file used when it boots (on (fd0) in the pic) and running these commands
Set root=(fd0)
Set prefix=(fd0)/boot/grub
Insmod normal
...But then I just get an error

---

### Post by Beauchmin on 2015-12-05
Sorry I just realized the pictures are sideways and upsidedown

---

### Post by Beauchmin on 2015-12-06
I just replaced the hard drive in the computer. I'm gonna install Windows on it and call it good, I'll probably wipe the old one when I find a means of doing so and start over. Thanks :)

---

### Post by yancek on 2015-12-06
If you decide at some future time to install Ubuntu or some other Linux with windows, make sure you have the windows installation medium available.  Your problem is you deleted the partition with Ubuntu and  the Grub boot files before verifying that you could boot windows.  You need to get the windows code in the MBR first.  If you are using UEFI on newer windows 8 or later) it's a different process.

---

