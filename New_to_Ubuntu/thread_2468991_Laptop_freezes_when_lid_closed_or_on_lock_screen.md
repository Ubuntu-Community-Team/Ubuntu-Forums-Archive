---
title: "Laptop freezes when lid closed or on lock screen"
date: 2021-11-16
forum: New to Ubuntu
---

### Post by foggybrain on 2021-11-16
Xubuntu 20.04.....
Cannot reawaken laptop when I close its lid, or activate lockscreen.  To get any response I have to crash out by removing battery etc.
Laptop then really struggles to get going........(Old laptop but new battery)
Not sure if Software or hardware issue, have tried reinstalling OS, and sometimes its frozen during install and I've had to repeat
battery remove crash out.

From task manager CPU & RAM are well in scope 10%- 30% CPU and 16% RAM so resources don't seem stretched

On third re-install I have found everything works ok as long as as switch off laptop when I've done. No changes to main settings just tweaks to colour scheme etc
so no silly settings that are upsetting things - all stock settings

---

### Post by tea for one on 2021-11-16
There is a recently created utility, designed to provide relevant information so that forum members can offer suitable advice.

[https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)

---

### Post by foggybrain on 2021-11-16
Thanks for reply.... report uploaded to  

View at: [https://paste.ubuntu.com/p/ghCKgkNvW2/](https://paste.ubuntu.com/p/ghCKgkNvW2/)

---

### Post by tea for one on 2021-11-16
A few comments about the report:-

[COLOR="#0000FF"]Line 62[/COLOR] - Current boot mode:   Legacy mode (alias CSM alias BIOS mode)
[COLOR="#0000FF"]Line 99[/COLOR] - /dev/sda1      vfat  511M  4.0K  511M   1% /boot/efi
[COLOR="#0000FF"]Line 107[/COLOR] - Disklabel type: dos
[COLOR="#0000FF"]Line 111[/COLOR] - /dev/sda1  *       2048    1050623    1048576   512M  b W95 FAT32
[COLOR="#0000FF"]Line 112[/COLOR] - /dev/sda2       1052670 1465147391 1464094722 698.1G  5 Extended
[COLOR="#0000FF"]Line 113[/COLOR] - /dev/sda5       1052672 1465147391 1464094720 698.1G 83 Linux

Your partition table is msdos and your partitions themselves are in msdos style, yet what happened to sda3?
You also have an EFI partition sda1?

Have you altered the UEFI/Legacy settings previously?

I would back up my data before doing anything else because it looks unusual.

---

### Post by foggybrain on 2021-11-16
I'm a linux newbie... so would not have done anything clever. There has been other linux distros before settled with xubuntu (with Win 7 as original OS.) All data backed up.  Is there a way to completely wipe disk of all weird crap and start completely fresh....is that the answer??

---

### Post by tea for one on 2021-11-16
> **foggybrain said:**
> All data backed up.  Is there a way to completely wipe disk and start completely fresh....is that the answer??

I think that is the right path to choose.

All your data is backed up - Excellent :D

Have you prepared (or do you still have) your Xubuntu 20.04 LTS USB device?

---

### Post by foggybrain on 2021-11-16
Yes have bootable usb with 20.04 on

---

### Post by tea for one on 2021-11-16
Splendid - here we go (Xubuntu only - Not dual boot)

_UEFI settings_

Disable Secure Boot
Disable Fast Boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled

_Xubuntu _

Boot into a live session in [COLOR="#0000FF"]UEFI mode[/COLOR] (how you boot determines the installation mode)
Double check that you are in UEFI mode - open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Check wifi, sound, graphics, mouse, keypad etc
Use gparted to create a [COLOR="#0000FF"]GPT[/COLOR] (GUID Partition Table)
Allow the installer to automatically create the necessary partitions (or your preferred configuration)
Sometimes (although very rare) internet connection prevents clean installation

Reboot and test your new system
Restore data if happy

---

### Post by foggybrain on 2021-11-16
Sorry, this is way out of my depth.  Is there a linux equivalent to windows format c:

---

### Post by tea for one on 2021-11-16
Your Hitachi drive will automatically be formatted during the installation process.
The only bit of pre-preparation is:-

Boot into a live session
Open Gparted > Device > Create partition Table > Select gpt

This will wipe all the data on the drive.

If this is not your intention then do not proceed.

---

### Post by foggybrain on 2021-11-17
Thanks for your help, but would not let me do this as it said there were three partitions?   However in my desperation and ignorance found a command "WIPE" 
and ran this till it wiped itself out in mid operation!!

I then reinstalled Xubuntu, and all seems OK now (at least I have had no freezes at all for while will now)
But I suspect you will shout at me for not doing it the right way, and maybe the HDD is not really
at its best, but at least its working

---

### Post by foggybrain on 2021-11-17
Reran diagnostics mentioned earlier and uploaded report

View at: [https://paste.ubuntu.com/p/K7dmCRZvyj/](https://paste.ubuntu.com/p/K7dmCRZvyj/)

---

### Post by vmpx on 2021-11-19
Try this:
> Replace in GRUB menu for 20.04 ”quiet splash” with ”quiet splash      nomodeset” (On the grub screen click select ‘*Ubuntu’ and press ‘e’)

---

### Post by foggybrain on 2021-11-26
Thanks to everyone who has given me helpful suggestions, all is now working!

---

