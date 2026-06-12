---
title: "Ubuntu Installer does not auto-detect Legacy boot Windows 11 installation"
date: 2023-01-20
forum: New to Ubuntu
---

### Post by itsentdev on 2023-01-20
[SOLVED]
Hi! I'm having an issue where the 22.04-LTS release of Ubuntu (standard) does not detect my Win 11 installation, which I would like to dualboot. When I used to use Windows 10, it auto-detected it, but now it doesn't.
details for my windows 11 install:
- The (windows) installer was bypassed to ignore CPU requirements and UEFI boot requirements
- It is a fully activated Windows 11 Pro
- My PC doesn't support UEFI boot, as far as I know. (It's a Dell OptiPlex 990)

When I attempted to manually partition the system, it wanted me to make an EFI System Partition - I tried this but it just stopped my pc from booting until I booted to USB and removed the Ubuntu partitions.
Why is this happening, and (more importantly), how do I fix it?

Also - my Windows partition is detected as 'Windows Recovery Environment' in Advanced features.

---

### Post by yancek on 2023-01-20
Linux systems such as Ubuntu will not mount hibernated filesystems as there is a great risk of damage.  Windows 10 had hibernation on as the default, not sure about 11.  I would check that first.  Read the information at the site from the link below.

[https://www.makeuseof.com/windows-11-hibernate-enable-disable/](https://www.makeuseof.com/windows-11-hibernate-enable-disable/)

Any computer sold in the last decade should be UEFI compatible.  If your windows is installed in Legacy mode, then you should install Ubuntu in Legacy mode.  Check the settings in your BIOS firmware to make sure Legacy/CSM is enabled.  Boot the Ubuntu USB in Legacy mode.  If you were prompted to create an EFI partition, you booted UEFI mode.  This is a setting in the BIOS.

Try booting the live Ubuntu USB and from a terminal, run the command below and post the output here.

```
sudo parted -l
```

---

### Post by tea for one on 2023-01-20
> **itsentdev said:**
> When I attempted to manually partition the system, it wanted me to make an EFI System Partition 
I assume that you were using Gparted to create space for Ubuntu?
Generally, it is better to use Windows Disk Management tools to manipulate NTFS drives.
After making space for Ubuntu, you should also allow chkdsk to run.

I found conflicting info about your Dell Optiplex 990 from 2011?
It may have UEFI but not Secure Boot?

It's worth double-checking the BIOS (or UEFI) settings.

---

### Post by itsentdev on 2023-01-20
Really? I do have an option in boot menu for UEFI boot... but I was told it couldn't use UEFI, so I always ignored it.
How do I boot to my Ubuntu USB in a different boot-type?

---

### Post by tea for one on 2023-01-20
> **itsentdev said:**
>  I do have an option in boot menu for UEFI boot... but I was told it couldn't use UEFI, so I always ignored it.
Just curious, who told you?
> **itsentdev said:**
> How do I boot to my Ubuntu USB in a different boot-type?
To boot in UEFI mode, you are looking for the entry UEFI:device name
i.e. UEFI followed by colon then the device name -  Sandisk or Kingston or Verbatim etc.
Does this attached image help?

---

### Post by Impavidus on 2023-01-20
Check Windows' FastStartup setting. That makes that Ubuntu can't see Windows. Use Windows tools to edit NTFS partitions and allow Windows to run its disk checks.

Some website tells me that that computer was released with Windows 7 preinstalled just a few months before Windows 8 was released, for which Microsoft demanded UEFI. Normally, it should support UEFI. Sometimes those early UEFI systems don't conform entirely to standards, making it harder to boot Ubuntu, but you already succeeded at booting the live disk.

Windows 11 is already installed (in legacy mode, I assume) and running Ubuntu and Windows in different modes makes things a bit hard. At the same time, dual booting Windows 8 or higher and Ubuntu in legacy mode is a bit fragile.

---

### Post by tea for one on 2023-01-20
I was trying to find if Windows 11 is supported in Legacy mode and, eventually, this appeared:-
> The following disclaimer applies if you install Windows 11 on a device that doesn't meet the minimum system requirements:
This PC doesn't meet the minimum system requirements for running Windows 11 - these requirements help ensure a more reliable and higher quality experience. Installing Windows 11 on this PC is not recommended and may result in compatibility issues. If you proceed with installing Windows 11, your PC will no longer be supported and won't be entitled to receive updates. Damages to your PC due to lack of compatibility aren't covered under the manufacturer warranty
From here [https://support.microsoft.com/en-us/windows/installing-windows-11-on-devices-that-don-t-meet-minimum-system-requirements-0b2dc4a2-5933-4ad4-9c09-ef0a331518f1](https://support.microsoft.com/en-us/windows/installing-windows-11-on-devices-that-don-t-meet-minimum-system-requirements-0b2dc4a2-5933-4ad4-9c09-ef0a331518f1)

I still think that the OP should see if Windows 11 can be installed on the Dell Optiplex 990 in UEFI mode?
It may prevent difficulty in the future and as noted by Impavidus "dual booting Windows 8 or higher and Ubuntu in legacy mode is a bit fragile".

If Windows 11 in UEFI mode is impossible, then we can offer relevant installation advice for Ubuntu in legacy mode.

---

### Post by Frogs Hair on 2023-01-20
Is secure boot disabled ?

---

### Post by itsentdev on 2023-01-21
I don't have Secure Boot, only UEFI boot. Thanks, though!

Thanks for the advice, after spending two days in Hiren's Recovery CD I successfully deleted my old system reserved partition and created a fully function EFI System Partition.
I'm now going to go and boot my USB in UEFI mode. Thanks for all the help, you're all really nice!

My device was an upgraded prebuilt, and the Windows 10 installation it came with was preinstalled legacy mode. When looking through Dell docs a few months ago, I found no reference of UEFI being applicable to such an old model.
I converted my W11 to UEFI boot, and will now go and install Ubuntu in UEFI. Thanks!

The PC is an upgraded prebuilt. The Windows 10 that first came with it was installed as Legacy boot, and when looking through Dell docs I never found any mention of UEFI booting being available.
I have already figured it out, though it took me a while, but thank you for your help!

Edit: Quick update, I currently am unable to install Ubuntu because when I attempt to cut 100gb off my C: partition, the Windows Disk Management software tells me that the 'parameter is incorrect', and there appears to be some sort of GPT table damage.
Any advice?

---

### Post by oldfred on 2023-01-21
Windows requires gpt to install in UEFI mode.
Ubuntu can install in UEFI mode to old (very old) MBR(msdos) partitioning, but really should not. 
Post this for each drive.
sudo gdisk -l /dev/sda

Also only shrink Windows using Windows tools and reboot as it wants to run chkdsk after any resize.
Then make sure Windows fast start up which sets hibernation flag is off. And if bitlocker make sure it is off.
Some more settings:
UEFI & Windows Settings for UEFI install  - tea for one 
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)

---

### Post by MAFoElffen on 2023-01-21
If he is running Window 11, from a PC that was made circa 2011, he has bypassed all Win11 installation requirements, so nothing should be assumed.

In Windows, start PowerShell in Administrative Mode
```

Select-String "Detected boot environment" C:/Windows/Panther/setupact.log

```
That will return the Boot mode Windows was booted in...

And fastboot can be turned off while still in Powershell
```

powercfg /h off

```

---

### Post by itsentdev on 2023-01-21
I managed to install ubuntu as UEFI, but my USB WiFi dongle isn't detected :(
I don't even have an settings page for wifi. should I make a new thread?

---

### Post by MAFoElffen on 2023-01-22
If you did, and put it in the networking section ([https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)), it might be better, though... And get more specialized help.
```

sudo lsusb -vvv

```

---

