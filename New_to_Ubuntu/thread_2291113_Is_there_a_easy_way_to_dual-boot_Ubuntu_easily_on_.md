---
title: "Is there a easy way to dual-boot Ubuntu easily on a hard drive? (USB)"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by Austin_Muckelrath on 2015-08-17
I already downloaded and transferred the Ubuntu ISO file onto my 32GB Flash Drive (thanks to Universal USB installer). Is there an easy way of doing partitions for Ubuntu with, I don't know, 64GBs for the Ubuntu partition only? I have a 500GB hard drive (409GBs free) alongside with 4Gs of RAM, and I thought about dual-booting Ubuntu alongside with Windows 10. I've never dual-booted in my life, so please keep this simple. I'm just starting getting into Ubuntu and I want to use it alongside with Windows (dual-booting).

---

### Post by ian-weisser on 2015-08-17
Preparing Windows (unlocking EFI, defragging, and resizing the partition in Windows) is the annoying and tedious bit for me.
Ubuntu can do nothing about those. You paid your OEM and Microsoft for those features.

After EFI and Windows are prepared so the installer can work, the installation process is simple and surprisingly easy.

---

### Post by rccharles on 2015-08-17
You may consider download the free Oracle virtual box.  You can run a copy of Ubuntu in the virtual box.  These are called virtual machines.  They act almost like real machines.  That way you can get familiar to installing Ubuntu.  You can try out partitioning to see how it works.  

You may want to load a few drivers in you virtual machine to improve performance. If the mouse don't track right, you need some extra drivers.

R
PS. On second thought, oracle is still getting virtual box to work with windows 10 a few days ago.  You may need to try the beta.

---

### Post by oldfred on 2015-08-18
Is Windows already installed?
Is system UEFI or BIOS. 
And if UEFI is Windows installed in UEFI or CSM/BIOS/Legacy mode?

I prefer smaller system partitions for both Windows and Ubuntu. And then a larger shared NTFS data partition. But with any Windows from 8, you must make sure fast startup is off.

I always use gparted either its own liveCD or the gparted that is on the Ubuntu installer to partition in advance. Then I have to use Something Else to choose (change button) the partition(s) I created as / (root) and format like ext4. If swap created in advance it auto finds it and uses it.

---

### Post by tristan16 on 2015-08-18
The Ubuntu installer should give you an option to install alongside Windows 10, and will let you resize the partitions for each OS. It's pretty straightforward. It's when you have multiple partitions or OSes already on a hard drive that things get complicated.

---

### Post by oldrocker99 on 2015-08-18
Creating a 32GB partition for the system ,/, will likely be all the room needed. The other partition of the drive is what /home should be mounted to. You can do it pretty easily with the installer and selecting "Something Else."

---

### Post by Austin_Muckelrath on 2015-08-18
So, it's pretty straight-forward? I went to disk management, right click on C drive and clicked "shrink volume"  32768 MBs (32 in GBs). Now I have 32GBs unallocated. Once I installed Ubuntu and clicked "something else," all I have to do is click "free space" and find "/", then install it? I'm still pretty confused about this.

---

### Post by oldfred on 2015-08-18
If you do not create a partition with gparted, you have to create it with the installer's + button. If created in advance you use change button.
Then you choose size if not existing, select / (root), select format and select ext4. Usually best to also have another small 2GB or so partition for swap. That is not formatted, but just selected as swap.

Lots of screen shots on process.
       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by ja-leesa on 2015-08-19
I remember being so nervous the first time I set up dual-booting on my computer, but it is really straightforward. If you've made the partition in Windows, this partition will pick up when installing Ubuntu. Pick the 'Something Else' option when asked about Ubuntu's install location, and you'll get a screen that lists all of your hard drives. I usually cheat and just figure out which partition I want by size, but the partitions will also be named too. '/dev/sda' is usually your main partition, and every other partition is going to have a number or letter after it (i.e. /dev/sda1, /dev/sdb). Your secondary partition will more than likely be something like '/dev/sda1', though I would verify the size of the partition too to make sure it's the right one.

The one thing I will say is that once you've dual-booted your computer, that's done. There is no way to undo this process other than re-formatting your computer again and reinstalling everything. I've learned to my dismay that the boot loader breaks if I delete the Ubuntu (or any Linux) partition. But if you're sure that this is what you want, or you don't mind re-installing everything later, have fun!

---

