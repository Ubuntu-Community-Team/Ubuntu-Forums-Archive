---
title: "UEFI and BIOS Legacy"
date: 2020-07-09
forum: New to Ubuntu
---

### Post by optimusprime11 on 2020-07-09
Hi,

I had successfully installed Ubuntu 20.04 server on my Intel NUC via M.2 storage. I noticed it was booting in UEFI and the world was all good. However I needed to boot from my SATA SSD to access a previous installation of Windows 10. I needed to boot in legacy to get Windows running. That all worked fine and I got what I needed. When I tried to enable UEFI again on the NUC, it would not find the Ubuntu UEFI boot. Ubuntu will now only boot in Legacy and upon booting it provides me with a 10 second count down in a GRUB screen allowing me to select from the following:
*Ubuntu
 Advance options for Ubuntu
 Windows 10 (on /dev/sdb1)

my ultimate goal is to format the SDD and use that for a VM of Windows 10. but that's for another day...

I'm new to UEFI but understand its superior to Legacy. Plus as I had it working before it's frustrating me that I cant get it working again. Perhaps I have a corrupt UEFI boot? I really don't want to format and start again! 

Any help would be very much appreciated.

---

### Post by tea for one on 2020-07-09
Are you sure Windows 10 is installed in Legacy mode?

Assuming that you can still boot into both systems, you can double check the installation mode.

In Windows 10 - System Information > System Summary > BIOS Mode (hopefully UEFI for Windows 10) 

In Ubuntu - Open a terminal and enter ```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
```

Secondly, what do you see if you press **F10** (boot device selection screen) when powering on the Intel NUC?

---

### Post by oldfred on 2020-07-09
For Ubuntu/grub to now boot in BIOS/Legacy boot mode, you have to have reinstalled grub. Or do you also have grub on old MBR drive?
There are two versions of grub, grub-pc for BIOS boot and grub-efi-amd64 for UEFI boot. 

Windows only boots in UEFI mode from gpt partitioned drives and UEFI really recommends gpt for UEFI. But Ubuntu does let you use MBR(msdos) with UEFI, but probably should not.

How installed systems boot, is controlled by settings in UEFI. How flash drive or external drive boots is controled by what you select in UEFI one time boot menu, usually two options if UEFI Secure Boot is off & USB boot allowed in UEFI settings.

My Asus system seems backwards as under CSM/BIOS/Legacy menu setting is the sub-menu setting to turn on UEFI boot. And my setting for 'UEFI or CSM' only boots in CSM/Legacy/BIOS mode. I have to use UEFI only setting.

So check UEFI settings, other posts have shown NUC to be somewhat unique. Which seems a bit strange as Intel created original EFI spec and turned it over to UEFI forum and are(were?) still involved. Left hand hardware & right hand Software do not communicate?

---

### Post by optimusprime11 on 2020-07-10
Thanks for the assistance guys.

My knowledge on start up is limited. My knowledge (albeit limited) is mainly within networking so please treat me a simpleton in this thread.

I ran the following:

```
chris@server:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"                         
Legacy boot on HDD                                                                                                      
chris@server:~$ [ -d /sys/firmware/efi ] && echo "Installed in UEFI mode" || echo "Installed in Legacy mode"            
Installed in Legacy mode   
```

This is the first time I have looked into the booting side of things and I am surprised to see it was installed in Legacy(?). Especially as I initially saw the NUC had this drive labelled in the UEFI boot list.

Is this something I can fix or change without starting again? (I really hope so).

---

### Post by tea for one on 2020-07-10
An Intel NUC can display both UEFI and Legacy installed systems.

In the UEFI system software, there is a checkbox for **Legacy**.

Your terminal output shows that Ubuntu OS is booting in Legacy mode.

Please confirm how Windows is installed?

Fire up Windows and go to - System Information > System Summary > BIOS Mode?

It is **important** that both systems are installed in the same mode.

UEFI mode with gpt partition is the modern way for both systems.

---

### Post by optimusprime11 on 2020-07-10
Just checked Windows 10 and it's showing BIOS mode: Legacy

---

### Post by optimusprime11 on 2020-07-10
now in the process of following this guide to convert MBT to GPT

[https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)

---

### Post by tea for one on 2020-07-10
You have _both_ systems installed in Legacy mode, which is fine but as you rightly mentioned in your original post

> I'm new to UEFI but understand its superior to Legacy. Plus as I had it working before it's frustrating me that I cant get it working again. Perhaps I have a corrupt UEFI boot? I really don't want to format and start again! 

Anyway, it now depends on what you want to do for the future.

If I were in your position, I would start from scratch and install both systems in UEFI mode.

If you decide to do this, please ensure that you have **restorable backups**.

There are methods to convert existing Ubuntu and Windows systems from Legacy to UEFI but, again, you will need **backups**.

---

### Post by tea for one on 2020-07-10
> **optimusprime11 said:**
> now in the process of following this guide to convert MBT to GPT

[https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10](https://www.windowscentral.com/how-convert-mbr-disk-gpt-move-bios-uefi-windows-10)

I hope that it helps.

Here is the Ubuntu guide

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Good luck

---

### Post by optimusprime11 on 2020-07-10
converting Windows MBT to GPT was very simple using that link and it worked, Windows now boots in UEFI... now working on Ubuntu.

Thanks

---

### Post by optimusprime11 on 2020-07-10
I have a few problems converting Ubuntu 20.04 to UEFI using Boot Repair (using this guide: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair))

Ubuntu will no longer boot in Legacy, i get the prompt: 'a bootable device has not been detected'. 
and the NUC cannot detect a UEFI boot so it does not provide with with the option of adding that disk into the list of bookable devices.

...I'm a little stuck now

---

### Post by optimusprime11 on 2020-07-10
none of that went to plan and i'm now reinstalling Ubuntu from scratch. problem is I cant seem to even run the bootable USB any more. the system hangs on an error: 

[ end kernel panic - not syncing: no working init found, try passing init= option to kernel. See Linux Documentation/admin-guide/int.rst for guidance. ]

I've had enough at this point. does anyone know of a good bootable USB image I can use to format the drive completely for peace of mind? I tried DBAN but that has a few errors

---

### Post by oldfred on 2020-07-10
What version NUC?

[https://askubuntu.com/questions/1208978/intel-corporation-device-80860d4f-is-not-supported-on-ubuntu-18-04-3](https://askubuntu.com/questions/1208978/intel-corporation-device-80860d4f-is-not-supported-on-ubuntu-18-04-3)
NUC10i7FNH
this Network adapter Intel Corporation Device [8086:0d4f] is new and supported by mainline Linux kernel since the 5.5 Linux kernel.

How to install Bionic on Hades Canyon (nuc8i7hvk/nuc8i7hnb) with Vega M GPU support  - using ppa
[https://ubuntuforums.org/showthread.php?t=2400400](https://ubuntuforums.org/showthread.php?t=2400400)
Updated drivers for Hades Canyon
[https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay](https://www.tomshardware.com/news/intel-graphics-driver-update-hades-canyon-amd-12-month-delay)
Intel NUC
[https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified](https://www.omgubuntu.co.uk/2018/06/intels-7th-gen-nucs-are-now-ubuntu-certified)
Certified ISO & Instructions
[https://www.ubuntu.com/download/iot/intel-nuc-desktop](https://www.ubuntu.com/download/iot/intel-nuc-desktop)
intel nuc - nuc5i5MYHE w/M.2 SSD 
[https://ubuntuforums.org/showthread.php?t=2376245](https://ubuntuforums.org/showthread.php?t=2376245)
boot into the EFI shell and manually point startup.nsh to the grubx64.cfg and run it
Running The Intel NUC6i7KYK On Linux With Skylake Iris Pro Graphics 16.10
[http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1](http://www.phoronix.com/scan.php?page=article&item=intel-sklnuc-pre&num=1)
Intel's Braswell NUC Trips On Fedora 22 But Runs Fine On Ubuntu 15.04
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Braswell-Fedora-Ubuntu](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Braswell-Fedora-Ubuntu)

---

### Post by tea for one on 2020-07-10
> **optimusprime11 said:**
> none of that went to plan and i'm now reinstalling Ubuntu from scratch. problem is I cant seem to even run the bootable USB any more. the system hangs on an error: 

[ end kernel panic - not syncing: no working init found, try passing init= option to kernel. See Linux Documentation/admin-guide/int.rst for guidance. ]

I've had enough at this point. does anyone know of a good bootable USB image I can use to format the drive completely for peace of mind? I tried DBAN but that has a few errors

Which Ubuntu image are you using?

Which tool did you use to make the bootable USB?

You can format the drive when you install, there is no need to use DBAN or anything else.

---

### Post by optimusprime11 on 2020-07-14
Hey, quick update. 
After a very frustrating time and coming back to it the following day it seemed the image wasn&#8217;t writing correctly to the USB stick. A solid format and rewrite with rufus did the trick and the server is now running UEFI, with fast and secure boot.
finally got there! As always, thank you all for your help.

---

