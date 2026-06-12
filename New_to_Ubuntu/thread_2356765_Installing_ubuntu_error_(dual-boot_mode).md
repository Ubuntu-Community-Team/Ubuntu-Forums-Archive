---
title: "Installing ubuntu error (dual-boot mode)"
date: 2017-03-26
forum: New to Ubuntu
---

### Post by ahmed98othman on 2017-03-26
Hello,

It is my first experience with Linux and Ubuntu, so I apologize if I forget important details.

I have been trying to install Ubuntu 16.04 and 16.10 (in dual-boot with win 10) but I cannot proceed to the installation process after choosing to "install Ubuntu" in the grub menu.
Every time I get error like this:
[IMG]http://i67.tinypic.com/2h4xmdv.jpg[/IMG]

And here is my laptop specs:
Processor:                  i7-6700HQ
Ram:                         16 GB
Discrete Graphics:      NVidia 960M
Integrated Graphics:  Intel HD Graphics 530
Primary OS:               Windows 10

---

### Post by Geoffrey_Arndt on 2017-03-26
Not a very Linux friendly PC - - dual hybrid graphics.

Here is a possible work-around if you are persistent . . . [http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)

---

### Post by oldfred on 2017-03-27
Have you tried nomodeset?
With UEFI boot you have to manually edit linux line.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 
    
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
You must have Windows fast start up or hibernation off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by ahmed98othman on 2017-03-27
> **Geoffrey_Arndt said:**
> Not a very Linux friendly PC - - dual hybrid graphics.

Here is a possible work-around if you are persistent . . . [http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html](http://www.webupd8.org/2016/08/how-to-install-and-configure-bumblebee.html)


Doesn't this solution want linux to be installed or I can log into it at least?

---

### Post by ahmed98othman on 2017-03-27
> **oldfred said:**
> Have you tried nomodeset?
With UEFI boot you have to manually edit linux line.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 
    
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
      
 [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) 
    
You must have Windows fast start up or hibernation off.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

I did what you said, by removing "quiet splash" and added "nomodeset" before the double dash. Unfortunately, I got the following error: 

[IMG]http://i67.tinypic.com/99e2hw.jpg[/IMG]

---

### Post by oldfred on 2017-03-27
Please please do not post screen shots in line.
You can easily attach with Forum's advanced mode and the paperclip icon.
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4 1024x768 if photo
[URL="http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098"]http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098
[/URL] 
While I do not normally suggest using a version before release,since your system is so new, you may need the very newest kernel & drivers available in 17.04.

 Daily builds
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Choose
[zesty-desktop-amd64.iso]("http://cdimage.ubuntu.com/daily-live/current/zesty-desktop-amd64.iso")

---

### Post by ahmed98othman on 2017-03-28
Some how I passed that problem and I got the loading screen, then this error appeared:
"(initramfs) unable to find a live medium containing a live file system"

---

### Post by oldfred on 2017-03-28
Can you press entry at that point?
I had similar issue with earlier version of 17.04 and it was totally locked up. Hard reboot was only choice and hard reboot is never recommended.

That can be related to a bad ISO, bad burn (copy) or just the brand of flash drive.

But what brand/mode motherboard?
Some require boot parameters. And most require various settings in UEFI.
My Asus Z97 required many settings. My Gigabyte z170 required some changes in UEFI.

---

### Post by ahmed98othman on 2017-03-28
.

---

### Post by ahmed98othman on 2017-03-28
I couldn't understand what you meant by "Can you press entry at that point?"

 I could turn off the computer or restart it by typing "poweroff" or "reboot".

 I use SanDisk 128 GB Ultra Flair USB, and rufus to burn the ISO ."I attached a screenshot so that you can see if I burn the ISO file correctly."

 I couldn't find my motherboard type, but I got this from cmd:

[FONT=arial black]Manufacturer: ASUSTeK COMPUTER INC.
Product: N501VW
SerialNumber: BSN12345678901234567        
Version: 1.0       

[/FONT]
 but here is my laptop specs page: [https://www.asus.com/Notebooks/ASUS-ZenBook-Pro-UX501VW/specifications/](https://www.asus.com/Notebooks/ASUS-ZenBook-Pro-UX501VW/specifications/)

---

### Post by oldfred on 2017-03-28
Sorry, thought it might be a desktop where you build it yourself with different possibilities of motherboards.
Brand and model is all that should be required.
Many have used Rufus from Windows to make good installers.

Have you updated UEFI/BIOS to latest from Asus?

Some at initramfs prompt can just press the enter key and it continues on after whatever errored out.

Have you changed UEFI settings to have fast boot off (different than Windows fast start up which also should be off), UEFI Secure boot off and drives set for AHCI.
You may have to also change settings to allow USB boot or UEFI USB boot.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Do you get grub menu with UEFI boot before the error?
If so many Asus need the  pci=nomsi boot parameter and most with nVidia need the nomodeset parameter. See post #5 above.

---

