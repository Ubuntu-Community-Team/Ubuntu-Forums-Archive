---
title: "Dual boot windows xp + ubuntu on seperate drives"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by hunter551 on 2008-08-04
I have windows installed on a SATA drive and recently added a 20gb IDE drive. I would like to install ubuntu on the IDE drive and be able to boot into both. When I install ubuntu I don't want it to change anything on the SATA drive, eg) windows bootloader. Is there a way that i can do this?

The way that I'm planning on doing is to set the IDE drive as master in the BIOS and then install ubuntu. This should automatically configure GRUB to give a choice of windows or ubuntu at startup right? If I do it this way does it affect the windows install in any way?

I just want to be sure that if it doesn't work out, I can unplug the IDE drive and have windows boot like nothing ever happened.

---

### Post by fiddledd on 2008-08-04
It was a while ago, but I did this myself for the same reasons as you. IIRC, I changed the boot order in the BIOS so that the Ubuntu drive was first in the list and installed grub to that drive. Just make sure you install grub to hda and NOT sda.

---

### Post by hunter551 on 2008-08-04
Does the installer actually give you a choice of where to install GRUB?

---

### Post by fiddledd on 2008-08-04
In the default options there's no choice, but at the confirmation stage there's an "advanced" button (unless it's been moved) where you can change where grub is installed.

BTW, I meant hd0 and sd0 in my first post.:)

---

### Post by hunter551 on 2008-08-04
[http://bp1.blogger.com/_uhA1e-8HtfQ/R7XE03dvDVI/AAAAAAAAAbw/6i6xfIcBJxU/s1600/ubuntu-installer-10-step-7-of-7-ready-to-install-02-advanced-options.png](http://bp1.blogger.com/_uhA1e-8HtfQ/R7XE03dvDVI/AAAAAAAAAbw/6i6xfIcBJxU/s1600/ubuntu-installer-10-step-7-of-7-ready-to-install-02-advanced-options.png)

So it should be like that?
Is hd0 the default?
Am I right in guessing that it uses sd* for SATA drives and hd* for IDE drives?

---

### Post by louieb on 2008-08-04
GRUB sees your drives as** (hd#)  **for partitions on the drive you refer to them by **(hd#,#).  Does not matter if the drive is ide or sata. **To be sure you can unplug the windows drive before you start the install. Of course if you do that you will have add windows to the grub configuration file manually. 

Ubuntu now sees most hard drives as **sd@ **doesn't matter if the drive is ide or sata. Only on rare occasions have I see a drive named** hd@**.  

btw: the advanced button is still there. Good luck and good reading here.

[Dualboot Two Hard Drives - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=179902")

---

### Post by Malac on 2008-08-04
As a further step you could try this once Ubuntu is installed and running this allows you to boot Ubuntu from the Windows Boot Menu :

   **Prepare the boot file for the Windows boot menu from Ubuntu**

[LIST=1]
[*]After completing the ubuntu installation, reboot .
[*] Open terminal and sudo su
[*] Use df to see which filesystem device holds /boot (e.g. /dev/hda1)
[*] Insert a DOS floppy disk and enter:
      mount -t msdos /dev/fd0 /mnt/floppy
[*] Substituting your /boot device, enter:
      dd if=/dev/hda1 of=/mnt/floppy/ubuntu.bin bs=512 count=1
[*] Remove the floppy and reboot to Windows
[/LIST]
     **Set up the Windows boot menu**

[LIST=1]
[*] Boot into Windows XP if you're not already there
[*] Insert the DOS floppy disk
[*] Copy the UBUNTU.BIN file from A:\ to C:\
[*] Open the System Properties window
[*] Click the Advanced tab
[*] Under *Startup and Recovery*, click Settings
[*] Click Edit to open the boot.ini file in Notepad
[*] Add this line to the end of the file and save:
      C:\UBUNTU.BIN="Ubuntu"
[*] Close the Startup and Recovery settings, open it again, and Linux should now appear in the *Default operating system* drop-down menu.
[*] Reboot and test it out
[/LIST]

Hope this helps.

---

### Post by hunter551 on 2008-08-05
Should i use grub, or the windows bootloader?

---

### Post by louieb on 2008-08-05
The real question is which one loads 1st GRUB or NTLDR (windows boot loader).  
Grub can't load window directly, it can pass control to ntldr which in turn boot windows.
And NTLDR can't boot Linux directly, it can pass control to GRUB which in turn boots Linux. 

My guess is that most people that dual boot  load Grub 1st.  And at least here you'll get better help if you use GRUB.

Choices all about choices: [http://en.wikipedia.org/wiki/Comparison_of_boot_loaders](http://en.wikipedia.org/wiki/Comparison_of_boot_loaders)

---

