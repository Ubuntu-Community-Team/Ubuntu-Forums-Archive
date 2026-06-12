---
title: "How to access my windows 7 installation"
date: 2015-09-23
forum: New to Ubuntu
---

### Post by SniperSkyBomb on 2015-09-23
Just installed Ubuntu onto my computer, wondering how to select which os i boot from.

---

### Post by grahammechanical on 2015-09-23
That depends on several things but you have not given us any information about your hardware or what the problem is.

If we install Ubuntu on a blank hard disk so that Ubuntu is the only operating system then when we start up the machine it will load into Ubuntu. We will not get a boot menu to select any other OS because there is only one OS.

If we dual boot Ubuntu with another OS we should get a boot menu that allows us to select Ubuntu or the other OS. There will be a 10 second time out to allow us to make a selection before Ubuntu will load.

So, a simple answer to your question would be to make the selection from the list in the boot menu. But I guess that you are not seeing a boot menu. And that could mean that Ubuntu is the only OS on that machine.

When we install Ubuntu we are asked to choose an option from this list

Install alongside [that is another operating system]
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something Else

Which one did you choose?

You could also run the Ubuntu Live session and from the live session desktop load the Disks Utility and take a screenshot of the partition layout that it shows you and include the screenshot in your post. Then we will have information about your hard disk and its partitions.

Regards.

---

### Post by SniperSkyBomb on 2015-09-23
I had already had an install of 7 on the hard disk. But i dont have a amount of time on bootup to select my OS. I did select something else when i instaled ubuntu because my installation of 7 wasnt recognized by ubuntu

---

### Post by SniperSkyBomb on 2015-09-23
[http://i.imgur.com/V7yHw7P.png](http://i.imgur.com/V7yHw7P.png)

partition screen. THank you for your time

---

### Post by oldfred on 2015-09-23
In Ubuntu's terminal have you tried:

sudo update-grub

Then does it show Windows was found and added to menu.
Or did you leave Windows hibernated. Or it needs repairs. Then you need your Windows repair flash drive to make repairs to Windows as grub only finds or boots working Windows.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

---

### Post by Geoffrey_Arndt on 2015-09-23
OK, . . . many dual-boots seem to go awry (e.g., go to sheet) because the new user is just not aware that Windows itself will defeat the full install of Ubuntu IF fast boot/hibernation is still active.   

Do you recall accessing your firmware setup (various setups depending on PC) whereby you can enable/disable fast boot, hibernation etc.?    On Win8 & 10 (not sure about 7), you can also disable hibernation via the control center "power" setup screens.

---

### Post by SniperSkyBomb on 2015-09-23
Thanks you all. The problem is solved. Thread will be closed.

---

### Post by uninvolved on 2015-09-24
For the sake of those who search (hey, it happens) you could tell us *how* you solved it and help the next person in line.

---

