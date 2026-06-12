---
title: "Yet Another Windows 8 and Ubuntu Problem"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by c5vetter on 2013-02-05
ALL,

Have bought new HP Pavilion g7z Laptop AMD Dual-Core A6-4400M 2.6GHz laptop and want to install / dual-boot Ubuntu 12.04 LTS. Have Ubuntu LiveCD, which I used on Windows 7 machine with no problems. 

I attempted to install on new laptop, and did a reboot when required, and appeared laptop hung. So, did a hard power off, and screen came up with choose Windows or Ubuntu, and clicked on Ubuntu and got an error of some sort. Clicked on ESCAPE key and it automatically took me to Windows. 

Appears Ubuntu was loaded, as now have a "F drive", which did not have prior to attempting install. So, am confused as to where to go from here.

---

### Post by cap10Ibraim on 2013-02-05
Can you post the exact error message you get ?

---

### Post by c5vetter on 2013-02-05
Okay, start computer and comes up with screen to choose an OS:

Choose Ubuntu and get the following:

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert windows installation disc and restart your computer.
2. Choose your language settings and click next.
3. Click repair your computer.

If you do not have the disc contact your system administrator or computer manufacturer for assistance.

File\ubuntu\winboot\wubildr.mbr

Status: 0xcv000007b

The application or OS couldn't be loaded because a require file is missing or contains errors.

ENTER = OS selection     ESC = UEFI firmware settings

If I choose Windows, then windows launches fine.

So, how/what do I need to do to get Ubuntu to launch?

---

### Post by cap10Ibraim on 2013-02-06
If Windows loads fine , I think you need to fix grub (reinstall it)

---

### Post by Mark Phelps on 2013-02-06
> **cap10Ibraim said:**
> If Windows loads fine , I think you need to fix grub (reinstall it)

NO ... NO ... look a the wubildr message!

This is a Wubi installation -- if you force the installation of GRUB, not only will that NOT fix this, it could possibly break Win8 so it won't work, either.

---

### Post by oldfred on 2013-02-06
If this is Windows 8 pre-installed then you have UEFI secure boot with gpt partitions. The issue is gpt partitions and wubi does not work with gpt partitions at the current time.

But with gpt partitioning there is no more the 4 partition limit, so adding partitions for Ubuntu is easy. But UEFI secure boot again has made it difficult.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. 

Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
Bit older, Mac & PC UEFI, note issues on some systems
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Another HP:
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

### Post by c5vetter on 2013-02-06
Okay, let me get this straight - can NOT use 12.04 LTS for UEFI, but MUST use 12.10 - is that correct? If so, will order the DVD and wait for that to arrive.

BTW - have disabled Secureboot

---

### Post by holy ghost on 2013-02-07
Brand new Ubuntu user here (and certainly no computer guru so pardon the poor explanation here) - had the exact same issue when I installed last night, in Windows 8 in the BIOS section there are some tricky settings where it will not boot from a disc with another OS and will give you this error message. When it gives you the two OS options there's a little option at the bottom to change settings, which will take you to some options, there is a settings option in DOS mode to change the default boot from a Windows OS - turning this off will allow you to boot from the Ubuntu DVD

You'll have to pardon my poor language here, I cannot go and double check as I deleted the bloated Windows OS right off my computer while installing :guitar:

---

### Post by oldfred on 2013-02-07
If you keep secure boot off, 12.04 should work. But it seems to vary a lot by vendor. Some vendors have not just implemented secure boot but modified UEFI to only boot Windows. Ubuntu used same secure boot key with 12.10 as Windows and some systems refuse to recognize it.

Also 12.04's next point release in a week or so will have the new grub2 2.00 that supports secure boot. So either download 12.10 or wait until next point release on 12.04.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule?action=show&redirect=PreciseReleaseSchedule)

       Also instructions for CD/DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

