---
title: "Ubuntu doesn't see my Windows 7 install"
date: 2015-02-15
forum: New to Ubuntu
---

### Post by will65 on 2015-02-15
Hi guys,

I want to dual boot Windows 7 Home Premium (x64) and Ubuntu. I downloaded the .iso for Ubuntu x64, used [Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") to put it on my USB drive, and then eventually managed to shrink my SSD using Windows Disk Management to leave 30GB of unallocated space. I restarted the machine and booted Ubuntu from the USB drive and tried to install it.

Firstly, it didn't recognise that I had any other operating systems installed. There was no option for installing alongside Windows. I'm as good as new to this, and although I've already done a search and read similar threads, I don't trust myself to blindly follow old instructions. I've popped into Ubuntu's 'try' mode and looked at the gpartition editor. It sees the different partitions. I then tried installing it by manually selecting the unallocated space, and selecting ext4 and / as the mount point (based purely on what I've read on other threads). It proceeded with the installation, but after it finished and rebooted, it went straight into Windows. There's no sign of the GRUB screen I was expecting, and although Windows Disk Management sees that the unallocated space is now a primary partition with the ext4 file system, it's still empty. Am I missing something?


I've not been able to find an answer in the documentation, and I don't trust myself to follow the instructions posted to other people's queries anymore. I've already had a little moment this morning. After struggling to shrink my C: drive by more than 5GB, I resorted to using Aomei Partition Assistant and ended up deleting something vital. Took me half an hour to fix the "bootmgr is missing" issue and scared myself a bit. Gonna be honest, from the perspective of a relatively experienced PC user, installing Ubuntu is quite scary 8-[

---

### Post by grahammechanical on 2015-02-15
> [COLOR=#000000] installing Ubuntu is quite scary [/COLOR]

Such is life for anyone trying to install another operating system on a machine with an already existing OS pre-installed. The other year I installed Windows 8 preview edition.

I thought it would be safe to do as I had two hard disks with different versions of Ubuntu on each of them. I reasoned, if Windows overwrites the Linux boot manager (called Grub) on the hard disk I am installing Windows 8 on I would still be able to load into Ubuntu on the second hard disk.

I was wrong. The Windows installer put its boot loader onto both hard disks. We would have the similar problems if we were doing things the other way around - installing Windows on a machine with Ubuntu pre-installed. But back to your situation.

Please run Boot Repair. It will be your choice if you accept the recommended repair but at this stage it is not necessary. Boot Repair will produce a report. You will get a URL to a web address where the report has been uploaded. Post the URL into this thread and some of us will try to figure out what can be done.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

A screenshot taken from a Windows utility showing the partition layout would also be useful.

Regards.

---

### Post by yancek on 2015-02-15
There is an option on the screen to set "Device for bootloader installation" and you will have a number of options there.  Do you remember what you selected?
You indicate you installed Ubuntu to an SSD, do you have other drives on the computer?  If you are using MBR to boot, you would need to install the Grub bootloader to the master boot record of that drive (the SSD) and set it to first boot priority.  It's possible to boot Linux from windows but not easily done.

> There's no sign of the GRUB screen I was expecting, and although Windows  Disk Management sees the unallocated space is now a primary partition  with the ext4 file system, it's still empty. Am I missing something?

That doesn't mean much.  In fact, I'm surprised it is even recognized as ext4.  A default windows install is incapable of reading a Linux filesystem so you probably have the installation and posting the boot repair suggested above is the next best step.

---

### Post by will65 on 2015-02-15
Thanks for the quick replies guys,

Here's the report from Boot Repair: [http://paste.ubuntu.com/10239426/](http://paste.ubuntu.com/10239426/)

Here's [the screenshot of Windows Disk Management showing the partitions]("http://i.imgur.com/QOxrTyl.png"). The one labelled Disk 2 is my SSD with Windows installed. You can see there's a 30GB primary partition on the SSD, and that's where I attempted to install Ubuntu. It was showing as unallocated before I attempted the install.

> **yancek said:**
> There is an option on the screen to set "Device for bootloader installation" and you will have a number of options there. Do you remember what you selected?

I looked at the options and selected what I thought was the new unallocated space. It was labelled as /dev/sda3 by the installer. It was about 32GB in size, so I figured it'd be the right one, especially since I've read Ubuntu seems to calculate available disk space differently to Windows. This would also mean that /dev/sda2 refers to the partition with Windows installed on it, and /dev/sda1 to the small Windows System Reserved partition on my SSD.

> You indicate you installed Ubuntu to an SSD, do you have other drives on the computer? If you are using MBR to boot, you would need to install the Grub bootloader to the master boot record of that drive (the SSD) and set it to first boot priority. It's possible to boot Linux from windows but not easily done

I have two old hard drives that I use as storage as well as the SSD. I'm not sure if I'm using MBR to boot. Not something I've come across before as far as I can remember.

---

### Post by oldfred on 2015-02-15
The old BIOS based computers can only boot from the MBR of a hard drive. The MBR is the very first sector of the hard drive and is not part of any partition. 
Only if you have another boot loader that allows boot of another system could you install grub to a partition as you have done. But Windows will not boot another install. Some third party Windows tools will convert Windows to allow it to boot, but installing grub to a partition is not recommended.

Since you have other hard drives in system, you could install grub to sdb and set BIOS to boot sdb first. Generally I suggest having boot loader in the same MBR as install, but with two installs on one drive only one can be in control of MBR.

If you use advanced mode of Boot-Repair you can choose the Ubuntu install and drive sdb to install grub into. Then in BIOS set sdb as default boot device. DO NOT run auto-fix as that just installs grub to every MBR.
If then you have issues with Grub you can in BIOS still choose sda and directly boot Windows.

---

### Post by will65 on 2015-02-15
Apologies for my ignorance oldfred, but before I start messing around again would you mind checking that I've understood what you're suggesting: I need to install Grub onto one of my other hard drives, then change the boot order in BIOS so that hard drive is chosen first. Grub will be able to see both the Windows and Ubuntu installs on my SSD, even if Grub itself is on a different hard drive. Is this correct?

> **oldfred said:**
> If you use advanced mode of Boot-Repair you can choose the Ubuntu install and drive sdb to install grub into.

Can you provide slightly clearer instructions on how to install Grub? I think the wording is throwing me a bit, but it sounds like you're suggesting installing Ubuntu on sdb as well as Grub. I reckon I've got the wrong end of the stick, but I can't see exactly what you meant here.

---

### Post by oldfred on 2015-02-15
There are parts of grub in many places. So when I suggest the Ubuntu install, that is where most of grub's files are. You have to mount the / (root) partition so grub can find the rest of grub & the kernels in /boot folder inside / and install just the boot loader portion of code to the MBR of sdb. Boot-Repair will do that in the advanced options menu. Default is all drives, DO NOT let it use default.

 GRUB 2 - GRand Unified Bootloader has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

---

### Post by will65 on 2015-02-15
> **oldfred said:**
> You have to mount the / (root) partition so grub can find the rest of grub & the kernels in /boot folder inside /

Have I already done this step when I originally installed Ubuntu to the new partition and selected / as the mount?

---

### Post by yancek on 2015-02-15
> Have I already done this step when I originally installed Ubuntu to the new partition and selected / as the mount? 		

You did but as you said in your earlier post, you selected to install the bootloader to the Ubuntu partition (sda3).  So how does the BIOS get to the sda3 partition?   You need code in the master boot record telling it that the bootloader is on sda3.  You have windows code in the master boot record and it can't do that.  It isn't capable of booting Linux, at least a default windows without third party software.  You can install to sdb as oldfred suggests or install to sda which will overwrite your windows boot code and probably create an entry for windows.  If something goes wrong and you don't have a windows installation medium, the second option could be a problem.

---

### Post by oldfred on 2015-02-15
You only have to manually do that if manually installing grub. You can manually just mount / and install grub from live installer, or you can do a full chroot which mounts all the needed partitions for a full uninstall/reinstall of grub.
But Boot-Repair automates all of that.

       [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System
[/URL]
 sudo mount /dev/sda3 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

      
 drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

     
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by will65 on 2015-02-16
> **yancek said:**
> You need code in the master boot record telling it that the bootloader is on sda3. You can install to sdb as oldfred suggests...

Sorry guys, but you're talking to a bit of a newb here, and a lot of this is over my head. In order to get Ubuntu to work, I only need to use Boot Repair to [place GRUB on sdb]("http://ubuntuforums.org/attachment.php?attachmentid=259998&d=1424023683"). Is this correct? All I need is a yes or no really.

---

### Post by oldfred on 2015-02-16
Yes, just install the grub2 boot loader to the MBR or specify the drive sdb which is then the MBR of sdb.

If you want to know a bit more about how BIOS based computers boot. This is an older version of Windows but generally how computers work. No need to read entire articule. 
       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by will65 on 2015-02-18
Hi again,

I put GRUB onto sdb and changed the boot order but for some reason [Windows doesn't appear](http://i.imgur.com/pbWTLSU.jpg) on the list of operating systems when GRUB loads. Any ideas why this might be, and how to fix it? I'd hate to have to change my boot order every time I want to switch operating systems :/

---

### Post by oldfred on 2015-02-18
First try this to see if it sees Windows and adds it. 
Did you leave Windows hibernated/fast boot? If so then the os-prober cannot see the Windows install to boot it.

sudo update-grub

---

### Post by will65 on 2015-02-18
> **oldfred said:**
> First try this to see if it sees Windows and adds it. 
Did you leave Windows hibernated/fast boot? If so then the os-prober cannot see the Windows install to boot it.

sudo update-grub

I'll try that and get back to you. Still finding my way around this new OS and getting it to work as I'd like. Got another problem now that is more concerning so I'm going to post about that in a separate thread and come back to this.

---

