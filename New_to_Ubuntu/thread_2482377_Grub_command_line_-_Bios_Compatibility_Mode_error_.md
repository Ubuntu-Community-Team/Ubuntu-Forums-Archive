---
title: "Grub command line - Bios Compatibility Mode error message when running Boot repair"
date: 2022-12-29
forum: New to Ubuntu
---

### Post by markahlstrom on 2022-12-29
Hi everyone - I'm new to Ubuntu and having some issues.  I am trying to overwrite an old laptop with Windows 10 previously installed with Ubuntu.  I only want Linux on the laptop (no more Windows!).  The laptop is a Dell Latitude 5590.  

I installed Ubuntu using a SD card image over the existing operating system.  It didn't seem to work the first time - it never opened when I restarted it - so used the SD card and I did it again.  The second time I overwrote the previous installation and got a fatal error - failure to install the boot data.  Now when I restart it takes me into the terminal line at grub>_

So I checked this online forum and learned how to make a live usb.  I have the live usb running now.  When I run boot repair and try to run the recommended repairs I get this message:[COLOR=#0000FF]


[/COLOR][COLOR=#000000]The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([/COLOR][www.sourceforge.net/p/boot-repair-cd]("http://www.sourceforge.net/p/boot-repair-cd")[COLOR=#000000]), after making sure your BIOS is set up to boot USB in EFI mode.

I ran boot repair info - see attached text file.  I've tried to reboot and modify my BIOS settings and disable legacy mode but then it does not allow me to boot into the LiveUSB and I just get to the command line at grub>

I've seen some similar problems listed on the forum here but they seem to be fairly specific situations with steps that I am not sure I need to follow.  So - I'm not sure where to go from here - I'm barely literate with computers and could use some help.  Thank you in advance.

[/COLOR]

---

### Post by oldfred on 2022-12-29
Most will not download an unknown file.
You should have followed suggestion by Boot-Repair to post the link to the summary report.

You have UEFI system.
But have installed in both BIOS/Legacy/CSM boot mode and in UEFI boot mode.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

The first partition bios_grub is for part of grub using BIOS boot on gpt partitioned drives.
The second partition ESP - efi system partition if for UEFI boot files.

You must be consistent, or always boot in UEFI mode, since hardware is UEFI. 
But then you must boot live installer/Flash drive in UEFI mode. It should show in boot menu as UEFI : xxx , BIOS boot would be just xxx. 
And then system default boots full install in mode you have set in UEFI settings. Make sure that is set for UEFI boot.

You may need to boot live installer in UEFI mode & reinstall grub with Boot-Repair, so settings are all UEFI.

---

### Post by tea for one on 2022-12-30
> **markahlstrom said:**
> I ran boot repair info - see attached text file.  I've tried to reboot and modify my BIOS settings and disable legacy mode but then it does not allow me to boot into the LiveUSB and I just get to the command line at grub
Power off the PC.
Attach your bootable USB.
Power on and tap (one second intervals) the dedicated key (F12 for Dell?) to access the one-time boot menu.
When you arrive at the boot menu, you should see an entry beginning with UEFI:name of disk (i.e.UEFI followed by colon followed by Kingston or Sandisk etc)
This will boot your live USB in UEFI mode.
Have a look at this image for more clarification

---

