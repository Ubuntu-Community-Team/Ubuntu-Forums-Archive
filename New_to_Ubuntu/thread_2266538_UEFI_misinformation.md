---
title: "UEFI misinformation"
date: 2015-02-23
forum: New to Ubuntu
---

### Post by kosak2 on 2015-02-23
Hi to all Ubuntu users here, I am a mediumly experienced Linux user, since 2006, yet my trouble now seems like a brick wall. 
I bought a new machine, Asus X550L:
iNTEL CORE I7
8Gb RAM
Nvidia Geforce 820m
and the (bad) Windows 8.1

As it is UEFI machine and I know Ubuntu currently supports secure boot, without any need of legacy mode, I would like to know if there is a way to access the UEFI menu as I do in Windows 8, (hold SHIFT while restarting) because to my understanding the pc doesnt allow any other way of entering setup while you are out of legacy mode. If I install Ubuntu and remove Windows, leaving Uefi, will I not be able to boot from USB or enter BIOS, in case anything needs changing?

I hope you respond quick, as I am stuck with this OEM cra*py Windows 
Thanks in advance

---

### Post by grahammechanical on 2015-02-23
UEFI is more than secure boot and there are other things that can effect a successful install of Ubuntu. Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Entering the UEFI boot system settings utility should happen before any OS or boot loader runs. Just as with the BIOS boot system settings utilities. Which key combination to use will depend on the key combination decided by the motherboard manufacturer. With my ASUS BIOS motherboard I press Del slowly again and again. Do you not have a motherboard user guide? Perhaps you can download a PDF version from the ASUS web site.

I understand that pressing shift during the early part of the boot process should bring up the Grub boot menu which is usually hidden on machines with only Ubuntu installed.

Installing Ubuntu in EFI mode and instructing the installer to erase the disk and install Ubuntu should not (and I do not think that it will) prevent you from entering the UEFI settings utility. Of course, once Ubuntu has loaded we do not have any utility to let us change UEFI settings. Maybe you get that with Windows 8.1. Maybe you think that is the only way to enter the UEFI settings utility but I do not think that is the case. Maybe, someone will confirm or disagree.

Regards.

---

### Post by kosak2 on 2015-02-23
Let me tell you that the thing is that I want to use UEFI, because at least in Windows it boots much faster than in legacy mode. Only when legacy mode is enabled can I press del key and enter bios. I just wanted to know if there was a way to enter UEFI from Ubuntu, as in Windows, cause otherwise I'll have to install Ubuntu in legacy mode and not benefit from UEFI. tHANKS for the reply

---

### Post by QIII on 2015-02-23
You don't enter UEFI "from" the OS.  That happens before control is turned over to the OS.  The same method of entry will apply unless the UEFI is set to only boot Windows when waking by the board's OEM.  I have seen articles about getting around that by making sure Windows actually shuts down..

The fast boot times are an illusion.  Fast boot skips some POST tests and Windows 8 does not really shut down.  It enters a modified hibernation mode.

You are waking Windows from that state, not booting it.  The fast "boot times" are a technical slight of hand.

---

### Post by kosak2 on 2015-02-23
You helped me realize thank you. I disabled fast boot in Windows just now, and I was able to enter BIOS pressing f2 on startup hehehe now just have to see a good distro with multi finger gestures support! Thanks so much

---

### Post by oldfred on 2015-02-23
You should also have a fast boot setting in UEFI that is different than the fast boot or always on hibernation in Windows.
The fast boot in UEFI skips the POST or checking what hardware you have, assuming no changes which usually is correct. But then it can be difficult to get into UEFI.
But you still should have a key to get into UEFI, sometimes only if from a cold boot not warm reboot.

I have an Asus motherboard and it has fast boot in UEFI and a setting for how many seconds that I can press a key. And most of the settings were under the CSM setting after I turned off the Windows boot, and changed to Other boot choice. Other boot seems like secure boot off.

Review all your UEFI settings.

Ubuntu does have a newer grub menu setting.  But I never have tested it. And not at UEFI machine currently.

```
### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
    fwsetup
}

```

You can also edit UEFI settings from live installer or Ubuntu with efibootmgr.
And many vendors now modify UEFI to only boot "Windows" by description in UEFI. That is not per UEFI standard. We have several work arounds, such as if only Ubuntu rename the grub entry from ubuntu to "Windows Boot Manager" and/or add the hard drive boot entry which still works to boot a hard drive as grub or shim to boot to grub menu.

Various workarounds for Windows only boot issues.
       [http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

---

### Post by kosak2 on 2015-02-24
Yeah that's true, I do have a fast boot option in the bios, yet it seems to pose no problem whatsoever if I press f2 before the asus logo. I guess I'll just leave it active, and I need to know something, is it ok to delete windows 8 entirely, replacing with ubuntu, and in the process neverturning off secure boot? Thanks for all the replies :D

---

### Post by oldfred on 2015-02-24
Several users have, but most dual boot.
A few have hard drives and remove drive with Windows and install a new SSD for Ubuntu only.
Not sure about your specific model. 
Because some have some minor issues, that for a few are not ok or have one application that they just cannot live without dual boot.

       Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)

---

