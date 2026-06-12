---
title: "Multiple Installation Problems"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by mallory2 on 2014-03-04
Hokay. So I've been attempting to get Ubuntu installed on my Windows 8.1 laptop because...let's face it...Windows 8.1 is even WORSE than Windows 8. However, I've run into a number of problems simultaneously. I did manage to get it to boot from a USB, but when I attempt to install it, at the Installation Type screen, no partition is selected...and honestly, I don't want a partition at all. In fact, I don't want anything to do with Windows 8.1. Now, it gets worse. When I attempt to click "change", it doesn't click. The mouse moves, but the screen won't click no matter what I do. I've tried numerous mice, tried the touch screen, tried the track pad. Nothing. I can't do anything. So at the moment, I'm at a loss and unsure if I can ever do anything with this (relatively new) machine again...

For details, my computer is a Toshiba Satellite laptop. Model: U845t-S4150

---

### Post by newb85 on 2014-03-04
Welcome to Ubuntu and the fora!

Before even looking at the partitions, were you not presented with a few options like "Install Ubuntu alongside Windows" "Replace Windows with Ubuntu" and "Something else"?  It sounds like what you want is that second option.

---

### Post by ajgreeny on 2014-03-04
No doubt with windows 8.1 this is a UEFI machine, probably with secure boot and fast-start enabled.

So, have a good long read through the info at [UEFI - Ubuntu Documentation]("https://help.ubuntu.com/community/UEFI") which may help you get started and then come back again if there is anything you don't understand.  It is very important you know how windows is instaled (legacy BIOS vs UEFI) as you must use the same for your Ubuntu install or you will find yourself having to go into the UEFI/BIOS setup each time you want to move from one OS to the other, and there is no certainty that both OSs will boot in that manner.

EDIT:
Whoops! I have just noticed that you don't want to keep Win8 so ignore some of my post below. Nevertheless it is still worth reading that linked page as it was very helpful to me when I installed my Xubuntu on this UEFI desktop with no Windows involved.

---

### Post by oldfred on 2014-03-04
Also we get many users who have one Windows application they cannot live without and then want to reinstall Windows. Best to have full backup even if you want to remove it entirely.

       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by mallory2 on 2014-03-04
Thanks for the replies.

For some reason, I did not see the "Install Ubuntu alongside Windows" or replace it options. I also changed the settings so that this would get past secure boot already. The main issue here is why I am not seeing the option to replace Windows.

---

### Post by oldfred on 2014-03-04
This Toshiba looks like an UltraBook, you also have to turn off Intel SRT, change to AHCI and depending on version installing may have to remove RAID meta-data that SRT creates. Otherwise grub does not install correctly as RAID may be a different install and that is only supported on server type install.

More details on Ultrabooks in link in my signature. You may have issues with dual video.

Some other Toshiba
 Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by mallory2 on 2014-03-05
So will Ubuntu not work well on an Ultrabook? Or is it still possible (with those changes) for it to work normally?

EDIT: I can't find IDE so I can change it to AHCI...

---

### Post by oldfred on 2014-03-06
Depends a lot on the system. 
Most work, but some have minor issues with one thing or another. Depends on how much you use that feature whether it is really a minor issue or a deal breaker.

And it normally takes several releases for Linux to catch up with new hardware. Intel offered many changes, not just video driver, but also kernel and other support software. But that has to get into Linux, then get into distributions, so 13.10 is a lot better than 13.04 was and soon 14.04 will be even better still.

---

### Post by mallory2 on 2014-03-06
Alright, well, I still can't get past the screen where it says that I need to choose a partition. It still won't let me click "change". I otherwise do not see any options for replacing Windows.

---

### Post by oldfred on 2014-03-06
Did you follow the directions on turning off fast boot and (but not required) secure boot.
And turn off Intel SRT and change to AHCI?

Or you may have to remove RAID meta-data that SRT uses. 
See link in my signature for more details for Ultrabooks.
First several links also vital for correct install.
And examples above for other Toshibas and in link on others with Intel SRT.

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

---

### Post by mallory2 on 2014-03-06
I installed Debian, then installed Ubuntu. Now Ubuntu's working, but Skype refuses to work, and it won't install any updates. Error after error.

EDIT: Alright, I reinstalled Ubuntu. It's working beautifully now! :)

Thanks for your help!

---

