---
title: "Can't boot from downloaded ISO USB."
date: 2014-09-13
forum: New to Ubuntu
---

### Post by riverguy99 on 2014-09-13
I cannot get a USB ISO to boot.
 

 The facts:  I have 5 laptops in our home and office.  All run 12.04 or 14.04.  Some dual boot with W7.  I configured all of these, plus more, by downloading Ubuntu, copying it to a USB drive and booting from that drive.  I have 6 USB drives with downloads from various Web sources.  Right now, I can get **NONE** of them to boot on **ANY** of the machines.  I get the same error messages each time, and they all point to no bootable data on the USB drive.  I have even tried to boot from these USB drives on two friends' machines just to see if they would work.  They did not.

 

 This all seems to point to corrupted downloads, but so many and all from different sources?  Plus even the very same old USB drives I used to install 12.04 and 14.04 on all of our machines don't work, either.
 

 One more thing, I also burned the ISO onto a DVD and tried to boot from that. Same error message.
 

 I am going out of my tiny mind here . . . anyone got any ideas?

---

### Post by oldfred on 2014-09-13
When you say you burned to DVD or copied to flash drive, did you copy ISO or install it?

Copying ISO will not work as that is just one large file. You need to install it which extracts the ISO and converts the device to bootable. You cannot just extract ISO either as it still is not bootable.

       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

    
       How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
Most find unetbootin works but some find pendrive works.

 Usb installer from Windows - pendrive
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)


 Howto help USB boot drives - sudodus
A tool that helps boot some computers from [other] USB boot drives - Chainloader
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Howto make USB boot drives 
[http://ubuntuforums.org/showthread.php?t=1958073](http://ubuntuforums.org/showthread.php?t=1958073)

There are some more advanced ways to directly boot an ISO copied to a flash drive using grub2 installed to flash drive separately and manually creating a grub boot stanza using loop mounts. 
[http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484](http://askubuntu.com/questions/388382/multi-partition-multi-os-bootable-usb/388484#388484)

---

### Post by riverguy99 on 2014-09-13
THANK YOU THANK YOU THANK YOU!   I've been so frazzled starting with a devastating backup system crash that in repeatedly try to create these boot USB sticks I spaced out the little step I always used:  Startup Dic Creator, right there on my Dash!  Sweet, simple utility and I just blew it off and copied the ISO to the USB.  Well, you made my day.  Thank you again!

---

