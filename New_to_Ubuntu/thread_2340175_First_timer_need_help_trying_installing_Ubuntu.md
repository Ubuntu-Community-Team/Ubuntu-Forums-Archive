---
title: "First timer need help trying installing Ubuntu"
date: 2016-10-16
forum: New to Ubuntu
---

### Post by Kushal_Adepu_ on 2016-10-16
Hello everyone I am a long time Windows user, and I need help  installing Ubuntu on the  ASUS FF6U-AS54 Laptop

System Specs: Intel I5
Eight gig ram 
256 SSD

---

### Post by Autodave on 2016-10-16
Have you downloaded the .iso file yet? Are you making this the only OS on the computer or are you going to dual boot it w/Windows?
What are the specs of the laptop?

---

### Post by Kushal_Adepu_ on 2016-10-16
As I already said the specs were Intel I five processor eight gigs of RAM and 256 GB SSD  i've already downloaded the iso file  I want Ubuntu to   be my only operating system   Cause I no longer like windows

---

### Post by Autodave on 2016-10-16
Sorry: I missed the specs. You will now need to make a bootable disk on the thumb stick or DVD. You cannot merely copy the file onto either: it has to be installed on the DVD or stick as an .iso file. Do you understand what I mean and do you have a program to do that?

---

### Post by Autodave on 2016-10-16
[URL="https://ubuntuforums.org/showthread.php?t=2174756&highlight=making+bootable+disc"][SOLVED] bootable USB and ISO images


[/URL]

---

### Post by Impavidus on 2016-10-16
Completely removing Windows and installing Ubuntu often leads to unpleasant experiences as you may find out that some programs you cannot live without (yet) don't work on Linux. So, unless you have a second computer running Windows, it's generally recommended to dual boot. That said, I don't dual boot with Windows. I've been running Linux only for years. Installing Ubuntu as the only system is easier than installing as dual boot.

Your hardware is good enough to run any flavour of Ubuntu. Your graphics hardware is missing from your specs, as is your wifi hardware. Those may make installation a bit harder, although eventually it should work. I suggest you try Ubuntu 16.04.1 LTS. Get the 64 bit version, labelled amd64.

Here is some information on creating bootable usb drives: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Kushal_Adepu_ on 2016-10-16
Yes I understand what you mean but what kind of program should I use and also know that most  pCs are shipping with windows 10 they have you UEFI  I know  have a legacy borrows works but not this new you UEFI  and I don't know how you change the boot order so it boots from sub stick  I wish I could Skype somebody and we could talk all this out

Is it possible I could Skype with one of you too

If anybody wants to talk to me via Skype I would really appreciate it thank you

---

### Post by oldfred on 2016-10-16
This is a forum where users post issues, and those that are familiar with issue may offer to help.
Then others can find solution and use it.

Please take a look at the link in my signature.

But most important parts are a full backup of Windows. You paid for it. And if later you want to sell it or have one Windows only program that you must use, then you may want Windows.
Turn off Secure boot in UEFI, and best to turn off fast boot in UEFI.
Use Windows to shrink NTFS partition if you do decide to dual boot and reboot immediately into Windows to let it run chkdsk.
Default install is just / (root) and swap. Many prefer to add additional partitions but only /home can be added during install and using the Something Else install option.

Some may show older version screens but process is same.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 10 screens or similar to Windows 8
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

