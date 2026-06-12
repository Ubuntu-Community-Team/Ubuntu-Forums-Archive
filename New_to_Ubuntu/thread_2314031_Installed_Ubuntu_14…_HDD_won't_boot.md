---
title: "Installed Ubuntu 14… HDD won't boot"
date: 2016-02-17
forum: New to Ubuntu
---

### Post by pete50 on 2016-02-17
I have a Ubuntu 14 CD that I used to "erase disk and install Ubuntu" on a Lenovo Ideapad y500 laptop.  Now when I try to boot, I get a black screen, then it goes into a BusyBox shell?

I can boot from the live CD to troubleshoot. What can I do to make booting Ubuntu from my HDD work?

---

### Post by oldfred on 2016-02-18
Did you install in UEFI mode?
Is Ubuntu now only system on Ideapad?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

 > Discovered that on my Lenovo, if I press F12 repeatedly on startup, it takes me into a Boot Order menu. If I select Windows there, it boots into Windows. I also found that to get into BIOS at startup on my Lenovo tower, you press F1 rather than the F2 I'm used to on other computers.
Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

---

### Post by Geoffrey_Arndt on 2016-02-18
Does your laptop have nVidia graphics?   If so, you may need to utilize the boot option "nomodeset" . . . _which provides a low resolution but useable display_.   This gives you the opportunity to install the nVidia proprietary drivers via:

"System Settings>Software & Updates>Additional Drivers"

How to do nomodeset:   

 To  boot with the 'nomodeset' boot parameter. 


   1).   For a PC with no other operating system - the Grub2 menu will NOT be displayed by default, so:
>     Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu. 


   If you are able to boot with this parameter, you can install a graphics driver from the "Additional Drivers" utility in the actual install. 
   [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2 
   [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) <-nomodeset option in detail

---

### Post by pete50 on 2016-02-18
> **oldfred said:**
> Did you install in UEFI mode?
Is Ubuntu now only system on Ideapad?
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


 Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://ubuntuforums.org/showthread.php?t=2230117](http://ubuntuforums.org/showthread.php?t=2230117)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

 
Lenovo Ideapad z585 Precise Installed wifi OK Dual Boot Win 7 no Sound SOLVED - other issues
[http://ubuntuforums.org/showthread.php?t=2170099](http://ubuntuforums.org/showthread.php?t=2170099)
[https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS](https://help.ubuntu.com/community/InstallUbuntu11.10OnLenovoEFI/GPT/WLAN/Power/BIOS)

No, i don't see an option on the install menu to install in UEFI mode.  i'll try to read more on that..
Yes, Ubuntu is the only OS on the machine now.

Here is the log you requested, thanks for your help!:  
[http://paste.ubuntu.com/15127661/](http://paste.ubuntu.com/15127661/)

---

### Post by pete50 on 2016-02-18
> **Geoffrey_Arndt said:**
> Does your laptop have nVidia graphics?   If so, you may need to utilize the boot option "nomodeset" . . . _which provides a low resolution but useable display_.   This gives you the opportunity to install the nVidia proprietary drivers via:

"System Settings>Software & Updates>Additional Drivers"

How to do nomodeset:   

 To  boot with the 'nomodeset' boot parameter. 


   1).   Fobra a PC with no other operating system - the Grub2 menu will NOT be displayed by default, so:
>     Hold down (right) SHIFT to display the menu during boot. In certain cases, pressing the ESC key may also display the menu. 


   If you are able to boot with this parameter, you can install a graphics driver from the "Additional Drivers" utility in the actual install. 
   [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) <- How to set NOMODESET and other kernel boot options in grub2 
   [-https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions") <-nomodeset option in detail

Thank you for the suggestion,
I followed these instructions and booted with the nomodeset parameter, but it just took me to a screen that said:
[FONT=courier new]Could not configure common clock
ACPI PCC probe failed.
ata1: COMRESET failed
ata1: COMRESET failed
Gave up waiting for root device. Common problems:
- Boot args ...
...
ALERT! /dev/disk/by-uuid/896b6a93-5572-4c23-9236-5ae17facb121 does not exist
Dropping to a shell!

BusyBox v1.21.1 ....
(initramfs) _
[/FONT]

---

### Post by Geoffrey_Arndt on 2016-02-18
Suggest you try to burn the latest iso for Ubuntu (15.10) . . . the newest kernel may take care of those errors per Launchpad feedback.    Worth a try imho.

---

### Post by oldfred on 2016-02-19
Looks like standard BIOS/MBR install.
System shows UEFI parameters, so how you boot installer UEFI or BIOS is how it installs.
With a large drive, I prefer smaller / (root) partition of 25GB or so and separate /home and/or /mnt/data partitions.

this thread says you also need another boot parameter:libata.force=noncq
[http://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error](http://askubuntu.com/questions/62295/how-to-fix-a-comreset-failed-error)

---

