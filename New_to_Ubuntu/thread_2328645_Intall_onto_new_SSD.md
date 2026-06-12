---
title: "Intall onto new SSD"
date: 2016-06-23
forum: New to Ubuntu
---

### Post by mailmatic on 2016-06-23
I want to install Ubuntu onto a new 240gig SSD. I am using a HP pavilion laptop running windows 10. I want to replace the SATA hard disk with a Kingston SSD. How do I go about initialising and formatting the new drive ready for installing Ubuntu. I have a 2.5 USB Caddy to enable me to do this so what software can I download to do this.

Many Thanks.
Tom

---

### Post by howefield on 2016-06-23
The Ubuntu installer should allow you to format and create the layout of your choice for the SSD once you get to the partitioning screen.

I prefer to load gparted (which is a partition editor) from the Live media and prepare the partitions before installing. Selecting "Something else" at the partitioning screen in the installation process would then let you mount those prepared partitions. 

What's the 2.5 inch caddy for ? Are you replacing the HDD or supplementing it with an external ?

---

### Post by mailmatic on 2016-06-23
Replacing the HDD. Can I put the new SSD into the caddy then format it using gparted before getting rid of the old HDD ?

---

### Post by howefield on 2016-06-23
Well yes you could :)

Seems an unnecessary extra step, but yes, you could.

---

### Post by Geoffrey_Arndt on 2016-06-23
Why not use the old HDD for extra storage, and have the SSD serve as host for the OS . . . root & system directories under (/) including your home directories, or if doing a separate (/home), keep it on the SSD (so the whole PC runs faster).   The HDD would then be for things like a media collection, other distro ISO's, etc.????

---

### Post by oldfred on 2016-06-23
If system is new UEFI system, and you use gpt partitioning, the Ubuntu installer will only install grub to drive seen as sda.
So if you do a full install to external it will still install grub to ESP - efi system partition on sda. You then  have to manually copy files from sda's ESP to sdb's ESP. And you have to partition in advance to include the ESP on sdb.

Easier just to install SSD to system, and use flash drive to partition and install Ubuntu directly.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
            Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html

[/URL] UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 

More details in link in my signature below.

[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]
[/URL]

---

