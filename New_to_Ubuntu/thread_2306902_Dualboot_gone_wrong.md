---
title: "Dualboot gone wrong"
date: 2015-12-20
forum: New to Ubuntu
---

### Post by lukas28 on 2015-12-20
Hello ubuntu forums,
yesterdy I finally decided to install ubuntu on my PC as I'm interested in programming etc. As there is already Windows 7 installed on that PC and I don't want to remove it yet, I chose to try a Dualboot installation. I followed some instructions found in the Internet and did it that way: I created a bootable USB drive and booted from it, then I created a Switch partition (my RAM is 8GB, so I decided to give it 10GB) and a new partition for my ubuntu installation (I think about 120GB).
My problem now is that the PC is always booting ubuntu and doesn't give me the chance to select Windows. I already checked from ubuntu, my files (including Windows 7 and everything else "old") are still there, so it should be possible (I hope). I also checked all the UEFI options but I can't find a option like "select boot partition" etc. there...

Any ideas..? :)

Thanks in advance,
Lukas

---

### Post by QIII on 2015-12-20
What instructions from the internet did you follow?  Unfortunately, what you have provided gives us no idea of the current state of the machine.

Just remember, there are a lot of instructions to be found for many things on the internet.  Unfortunately, much of that is simply wrong.  :)

---

### Post by lukas28 on 2015-12-20
I followed those instructions (they are in German though): [http://www.pcwelt.de/ratgeber/Schritt-fuer-Schritt-Ubuntu-Dualboot-von-Windows-und-Ubuntu-8707012.html](http://www.pcwelt.de/ratgeber/Schritt-fuer-Schritt-Ubuntu-Dualboot-von-Windows-und-Ubuntu-8707012.html)
In short I did the following:
1.) create a bootable USB drive using the "Universal USB Installer"
2.) change UEFI boot row to USB drive first
3.) restart the PC booting from the USB drie
4.) In the installation assistent choose "make something different" (I'm not sure if it's that in english)
5.) using that kind of partition managment assistent to take some space from the (until then the only one) Windows partition (of course not so much it harmed the already used space)
6.) using the new free space to create two new partitions (like mentioned above): 10GB switch partition and 120GB new partition (ext4 journal) and install ubuntu on it from the usb drive

I hope this helps you!
Thanks and greetings,
Lukas

---

### Post by QIII on 2015-12-20
"Do something else" is a better English translation.  :)  A German website, by the way, isn't a problem for me.

Did you see the section "***Partition verkleinern***"?   The part that says it is best to reduce the size of the Windows partition in Windows?  I would say that changing the size of the Windows partition ***must*** be done with the Windows partition manager.

Did you shrink your Windows partition using the tools in Windows, or did you do that towards the end with the Linux partition manager?

---

### Post by lukas28 on 2015-12-20
Er...I used the partition manager which comes with the ubuntu installation (if that's the Linux partition manager then yes, I used that one instead of Wndows's own...)

EDIT: Coul it work to simply uninstall Ubuntu, change the partitions in the Windows partition manager and re-install Ubuntu? Of course not without making a backup of the whole harddisk before..

---

### Post by yancek on 2015-12-20
> Coul it work to simply uninstall Ubuntu, change the partitions in the Windows partition manager and re-install Ubuntu?

No.  You can't "uninstall" an operating system the way you do an application.  You can format the partition and re-use to install.  How are you going to change the partitions in the windows partition manager if you can't boot it?  Do you have a windows installation disk?  If so, you can use the repair option on it to install windows code to the MBR.  Are you using MBR or UEFI?  The standard with windows 7 is MBR but??  If you use MBR for windows, you must also use MBR for Ubuntu.  If you use UEFI on one system you must also use it on the other.

If you get the windows boot code repaired and are unable to boot it, you will probably have to reinstall Ubuntu as it is extremely difficult to boot any Linux system from windows.  I would also suggest that you resize from windows running the Disk Management tool in windows 7.  After doing this reboot and run chkdsk at least once.  It might be a good idea to defrag also.

---

### Post by ajgreeny on 2015-12-20
You can't "simply uninstall Ubuntu" as it already has installed grub to your machine by the sounds of it, and you now really need to restore the Windows bootloader files in order to boot to Windows.  I no longer use Windows so can't tell you how to do that now but I do know that it requires either an install DVD for Windows, or the DVD(s) that you are prompted to make when you first boot Windows.

See Boot-Repair in my signature and follow the instructions to install it to your live Ubuntu system (or even to your installed Ubuntu system) and run the Boot-info script.  Do not run the default repair at this time, just the script and paste back here the pastebin link you get from the script.

EDIT:
Ninja'd by yancek!

---

