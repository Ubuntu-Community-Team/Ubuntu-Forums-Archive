---
title: "USB not connected in Windows Partition"
date: 2011-12-20
forum: New to Ubuntu
---

### Post by allenh on 2011-12-20
Hi, I'm a newbie and have installed Ubuntu 11.10 on my laptop and because of it's shortcomings (won't recognise my printer, won't load certain software designed for windows)  I have reinstalled windows XP in a partition using VBox.  I can't copy and paste files from Ubuntu to XP and the USB is not connected so I can't move any files in at all without perhaps cutting a disc (not convenient). I have tried to use the manual to fix USB problem but can't understand or get any info on how to 'add user to vboxusers group which might fix the problem.  I need simple directions without the presumption that I understand the jargon.

---

### Post by cortman on 2011-12-20
> **allenh said:**
> Hi, I'm a newbie and have installed Ubuntu 11.10 on my laptop and because of it's shortcomings (won't recognise my printer, won't load certain software designed for windows)  I have reinstalled windows XP in a partition using VBox.  I can't copy and paste files from Ubuntu to XP and the USB is not connected so I can't move any files in at all without perhaps cutting a disc (not convenient). I have tried to use the manual to fix USB problem but can't understand or get any info on how to 'add user to vboxusers group which might fix the problem.  I need simple directions without the presumption that I understand the jargon.

To copy/paste: You need to install "guest additions" on the VBox. With the virtual machine open go to Devices>Install Guest Additions. The VBox should take you through it from there.
To access USB: Go to the menu on the top and select "Devices>USB> and select the USB device you want to use. This will unmount it in the host OS and mount it in the VBox.

---

### Post by lechien73 on 2011-12-20
Hello & welcome to the forums,

Normally connecting a USB device in VirtualBox is as simple as clicking on the **Devices** menu, selecting **USB Devices** and then choosing your connected USB device (as in the attached screenshot). Is this not working for you? If not, please post a reply back and we'll do our best to help.

What printer do you have? You can often get rapid assistance from the forums here if you post your problem.

Finally, I understand your frustrations as a new user, but it's important to remember that Linux isn't Windows. More Windows software will run under Linux than the other way round! But much Windows software won't work - it's not a shortcoming of Linux, but just the fact it's a different operating system. There is much software available that is quicker, easier to use, and compatible with its Windows counterpart. Just check the Ubuntu Software Centre, or ask here - many who post to this forum have years of experience with excellent alternatives to Windows-based software.

---

### Post by anewguy on 2011-12-20
You will need to be sure you have set your userid to be part of the vboxusers group, and you need to create at least 1 USB filter in VirtualBox for the machine - just create a filter and leave everything empty.  You need to be in the group to access USB, and you need to create at least 1 filter to use USB - an empty filter just pretty much says "use any USB device".  By doing this the devices become available.


Dave ;)

---

