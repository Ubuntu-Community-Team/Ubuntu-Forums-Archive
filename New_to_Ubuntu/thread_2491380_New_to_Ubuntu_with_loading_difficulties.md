---
title: "New to Ubuntu with loading difficulties"
date: 2023-10-06
forum: New to Ubuntu
---

### Post by bentley58 on 2023-10-06
Hi out there. I am brand new to Ubuntu. I got a disc with Ubuntu 22.04 on it, after changing the bios settings to boot from disc I had to reboot my laptop (old one - Lenovo ideapad 510) Eventually Ubuntu came up and gave me a choise of wiping out windows 10 and loading Ubuntu in its place. Being sick and tired of windows with a disc capacity issue - 100 % for long periods = very very slow OS - I chose this. I went through the loading procedure quite fine and came to the end and it asked me to reboot my laptop. That was the end of my Ubuntu experience. Why is it so hard to get to even see the Ubuntu OS. Some images of my journey if they help. Where do I go from here?
And before anyone says it - Yes I know it was a dumb move to remove windows as well - it just seemed good to kill 2 birds with one stone. Get rid of windows and load Ubuntu.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292827&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292828&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292829&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292830&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292831&stc=1[/IMG]

---

### Post by oldfred on 2023-10-06
Please do not post screenshots or images in line. Just attach.
Not everyone has high speed Internet.
 If you use the Forum's advanced editor, you can use the paperclip icon to attach screenshots or other info. Post #4 , also no larger than1024x768 if photo
[https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](https://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)
Your last screen looks like you have booted past grub boot issues & are into driver issue(s).

Did you install choose to install the optional restricted drivers as part of install? Ubuntu has the nVidia drivers available, but they are not automatically installed. Some do not want proprietary software installed. 
If not can you get grub menu and boot second entry or recovery mode to command line.
If only one install, you have to press escape just after vendor logo & before grub menu normally appears to get grub menu. 

If you turn internet on, you can just installer nVidia driver.
sudo ubuntu-drivers autoinstall

If wrong nVidia driver installed, you must purge first.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by rifqilubis on 2023-10-06
> **oldfred said:**
>  

If you turn internet on, you can just installer nVidia driver.
sudo ubuntu-drivers autoinstall




how about amd drivers? does it auto install?
if it is, how to check that my amd driver are already installed?

---

### Post by mikewhatever on 2023-10-06
It is a bit of an undertaking to understand what the OP means or wants. It looks like an installation was attempted, and then a reboot is stuck at the splash screen, but I am not sure. There are no hardware specs or any other useful info to troubleshoot.
So, where dowe go grom here?

---

### Post by oldfred on 2023-10-06
Google tells me that specs for Lenovo ideapad 510 are Intel CPU & nVidia graphics.
Is your model different? If so post details.

If really AMD, all those drivers should be installed, but I do not know details as AMD seems to have a variety of versions, some obsolete.

---

### Post by bentley58 on 2023-10-07
Many thanks to all that have contributed, I really appreciate it. While talking to a friend I have since discovered (when he used a disc diagnostic tool) that I have a section of the original HD that is damaged. So I have bought a solid state HD (easy to change in that laptop) have reinstalled Windows 10 & drivers and will be using an external HD with Ubuntu on it.
And to the admin staff - I will attach images rather than load into text.

Many thanks

---

### Post by oldfred on 2023-10-07
Depending on version of Ubuntu, it may use the Ubiquity installer which has this very old bug that is only critical on external drives. But many of us have multiple drives and want grub's boot files on the same drive as the install, not always the "first" drive.

Posted work around to manually unmount & mount correct ESP during install #55 or( #23 & #26)
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Probably easier for newer users:
Remove esp flag from Windows before install to second or external drive - Tim Richardson
[https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator) & 

Be sure to use gpt partitioning, if partitioning in advance. Gparted still defaults to MBR, not gpt.

---

