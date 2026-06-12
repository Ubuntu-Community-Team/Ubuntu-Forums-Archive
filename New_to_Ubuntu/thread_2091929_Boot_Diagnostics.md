---
title: "Boot Diagnostics"
date: 2012-12-06
forum: New to Ubuntu
---

### Post by philpense on 2012-12-06
Have a Lubuntu USB install that worked flawlessly for weeks.  It now proceeds to the splash screen and persists indefinitely.  Created another Lubuntu USB and find the same thing. Is there some way to get to an error log -or- is there any diagnostic app I can load on a second USB to query the first?  Guidance sought

---

### Post by oldfred on 2012-12-06
If the error is before the grub menu then this lets us see if system is configured correctly.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
If after grub menu and if you are getting to splash then it is after. First try removing splash quiet from menu entry and see if you can spot some driver with error. Last entry is not always the issue and often difficult to spot. But log files have all those same lines.

You can mount other install and look at log files for errors, repeated tries at loading a device and then failure, or very long times for an entry.
Logs are in 
/var/log
There are a lot and some sub folders for even more. But demesg is the boot log. (not boot log for whatever reason).

So from another install or liveCD/flash etc. Change sda6 example to your other install:
       sudo mount /dev/sda6 /mnt
    gksudo gedit /mnt/var/log/dmesg

Edit you said Lubuntu. So you probably do not have gedit. Use Lubuntu default editor or sudo nano.

---

### Post by philpense on 2012-12-07
Much thanks for the timely reply.  Total novice with Ubuntu/Lubuntu and do not think I can perform any of your recommendations because the Lubuntu splash screen remains as long as the machine is on.  This is a native windows 7 64bit notebook and I can launch this BIOS.  My thinking was that through the BIOS the Lubuntu files on the USB could somehow be queried and possibly remedied.  Additionally, this machine has UEFI the successor to BIOS.
 
I have a netbook that was working well with Lubuntu and that too, will no longer boot.  For this machine I am looking for a way to direct install.  I am aware that when Lubuntu booted to the desktop there was the install option.  Wondering if there is a way to prepare a USB so that booting to BIOS would allow an install option.  Hoping for your continued support

---

### Post by oldfred on 2012-12-07
Are you booting with UEFI or in BIOS mode. If Windows 8 was preinstalled it will be UEFI, but older systems even with UEFI may still be booting in BIOS mode.

You should be able to use UEFI/BIOS to boot flash drive or CD you used to install and then add Boot-Repair and run its report.

If Windows boots and you do not have LiveCD or flash you can create a new one. Either download the full Boot-Repair SecureRemix or a new copy of Ubuntu. If UEFI you need 12.10 64 bit.

       Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by audiomick on 2012-12-07
> **philpense said:**
>  My thinking was that through the BIOS the Lubuntu files on the USB could somehow be queried and possibly remedied.  Additionally, this machine has UEFI the successor to BIOS.

> **philpense said:**
> Is there some way to get to an error log -or- is there any diagnostic app I can load on a second USB to query the first

What oldfred posted is exactly what you are asking for, and the easiest way to get it.
Go back and look at this one again
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
and you will see that it refers directly to creating a bootable USB with the boot repair .iso.

This
> I am aware that when Lubuntu booted to the desktop there was the install option.
would indicate that you were booting into, or have at least once booted into the "try without installing" option on the installer. That is the "live" environment. Anyway, doing a "direct install" as your refer to it is a matter of installing from the USB or CD that is created from the .iso on the Lubuntu site onto the drive of the laptop and not onto a USB device. What is it exactly that you need explaining about that process?

edit: oops, oldfred beat me to it again...

---

