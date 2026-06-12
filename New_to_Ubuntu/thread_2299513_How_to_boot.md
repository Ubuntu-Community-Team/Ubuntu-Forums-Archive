---
title: "How to boot"
date: 2015-10-19
forum: New to Ubuntu
---

### Post by Lucas_Winther on 2015-10-19
So i installed ubuntu 15, the newest version. But when i installed it, it asks me to restart. And when i restart my PC, it boots into my USB menu and asks if i wanna try, install, OEM install or check a CD. I can change it to boot from my OS bootloader, but then it starts windows start reperation.

EDIT
I have found out that i by pressing escape 2 times can come to a menu where instead of saying try, i can launch ubuntu. But when i launch it, the screen is all wierd to the left.

---

### Post by buzzingrobot on 2015-10-19
Can you outline how you did the install, what you saw on screen, where you acquired the install image and how you burned it to USB?

Also, are you using 15.04 or the yet unreleased 15.10?

Your description of what you see after restarting reflects  what you would see in the installer if you deliberately trigger the  display of those additional options. If you see those options after an install and after restarting with the install media removed, something has gone wrong with the installation.

It sounds like you are trying to dual-boot?  Correct?

At the end of the install process, you are prompted to remove the installation media (USB stick or DVD) and press return.  If the install was successful, you will boot into Ubuntu.

---

### Post by Lucas_Winther on 2015-10-19
I chose english, connected to network. I chose to install third party software + downloading updates while installing. When im done i't says nothing about removing USB. i am trying to dual boot. If i remove the USB it says the launcher crashed. I at this point dont care about dual booting i just want linux(ubuntu). Im installing ubuntu 15.04

---

### Post by buzzingrobot on 2015-10-19
From your first post, this:  > when i restart my PC, it boots into my USB menu and asks if i wanna  try, install, OEM install or check a CD. I can change it to boot from my  OS bootloader

With Ubuntu, those are installer options that are only displayed if the machine is booted into the install image (only possible if the USB/DVD is attached) and the user takes a specific action to trigger their display.  If the USB is not attached and you still see those options on a reboot, I have no explanation. 

When an install finishes successfully, you will see a message that says the installation has finished. If you installed from the "Try" mode, the message will say you can "continue testing" until you restart. If you went directly to the "Install" option, the message will just prompt you to restart.  In both cases, the GUI displays fades away and you see another prompt to remove the installation medium and press Return.

Did you see all the screens displayed here? ([URL="http://www.ubuntu.com/download/desktop/install-ubuntu-desktop"]http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)


[/URL]

---

### Post by Lucas_Winther on 2015-10-19
I did but if i remove the USB it boots into Windows Bootloader. I have seen all the screens you mention. Thanks for helping me this far :D

---

### Post by yancek on 2015-10-19
You don't indicate which version of windows you have installed which is significant since windows 8 and later probably use UEFI to boot.  If that is the case, you need to install Ubuntu using UEFI.  To get that info, boot the Ubuntu installation medium and go to the site below and and download and install boot repair and run it according to the instructions on the site.  Select the option to Create BootInfo Summary and post the output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Lucas_Winther on 2015-10-19
The text is kinda long so i will just send the link - [http://paste.ubuntu.com/12861706/](http://paste.ubuntu.com/12861706/)

EDIT:
I ran the bootloader repair and now i can start up ubuntu at a start menu liek the other, but with a start ubuntu button. But can i make it so it automatically goes into the start screen?

Thanks for all the help so far :D

---

### Post by yancek on 2015-10-19
> I ran the bootloader repair and now i can start up ubuntu at a start  menu liek the other, but with a start ubuntu button. But can i make it  so it automatically goes into the start screen?


I'm not really sure what you mean.  Generally on boot, you will see the Ubuntu option and the Advanced Options for Ubuntu.  Your Timeout is set to 10 seconds and will boot the first option after that time unless you change it or hit the Enter key.

---

### Post by Lucas_Winther on 2015-10-19
My system would not boot on it's own. Therefore i got the impression that the USB had to be plugged in, cause everytime i plugged it out, it crashed. When i ran the repair, it did something so my computer could boot by itself.

---

