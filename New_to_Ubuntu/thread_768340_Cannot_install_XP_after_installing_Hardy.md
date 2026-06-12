---
title: "Cannot install XP after installing Hardy"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by coderdb on 2008-04-26
I've decided to try a dual-boot system with XP and Hardy. Despite my best efforts, there are some things I do need Windows for. :oP Having just installed Hardy a few days ago, I popped in my XP SP2 CD today and...I have no HDD. There are 2 in my laptop, one for each OS. Tried with my Vista HP CD, and it sees the HDDs, but won't let me install, even though I've deleted, created and formatted a new partition on the second drive.

I was able to do this when running Gutsy, but I have no idea why it won't let me do this now. I've tried reformatting the second drive to FAT32 under gparted too, and nothing seems to work.

---

### Post by wpshooter on 2008-04-26
If it were me and assuming there is nothing on the hard drives that needs to be saved, I would use [www.killdisk.com](www.killdisk.com) to completely WIPE both drives and then I would install XP first on the #1 drive and then I would come back and install Ubuntu on the second drive.

Good luck.

---

### Post by nicedude on 2008-04-26
I agree with the above idea, but also you may be having trouble if you used gparted to format the partitions you are trying to install on. I would delete all the partitions on the drive you want to install XP on then use XP setup disk to create new one to install to. Windows install seems to like partitions made by Windows.

---

### Post by coderdb on 2008-04-26
I did try the wipe-everything-off-the-drive thing, but that was with gparted, and also with the Vista CD. I'll try killdisk and see what happens though - will let you know!

---

### Post by PartisanEntity on 2008-04-26
I would also be careful when installing XP after you have installed other operating systems, Windows operating systems are notorious for ignoring what's on the HDD already and attempting to use their oboot loaders with only Windows as the choice. Not sure if Vista does that too.

---

### Post by coderdb on 2008-04-26
I've used killdisk to erase totally both of my laptop HDs. And the XP CD will still not detect them. Ubuntu works fine though (I'm using it now). I'm very confused...any ideas?

---

### Post by coderdb on 2008-05-05
No ideas from anyone? I'm just concerned in case it's a hardware problem with my laptop, for some strange reason...

---

### Post by Dani Filth on 2008-05-05
I'm dualing boot too, with Ubuntu installed first, then XP. I dualed since 7.10 and it ran smoothly. Now I upgraded from 7.10 to 8.04 and still be able to boot to both OSes (Ubuntu & XP). Not sure if you've checked [this](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) out, but that the guide which I followed to dual boot on my laptop.

---

### Post by coderdb on 2008-05-05
It's not that it won't dual boot. It just won't install. The XP SP2 CD I use cannot see any of my HDDs apart from the external, and the Vista CD won't install on any of the internal ones. This is after I've used Killdisk to totally erase everything on both of my drives.

I know that the XP CD works because I can install it as a virtual machine, and I know the Vista DVD works because I did have it installed at one point, before moving to Linux. My laptop just doesn't seem to show either of them the HDs inside. But Linux can see them (and install to them) fine, both Hardy and Gutsy.

---

### Post by coderdb on 2008-05-06
Still no ideas?

---

### Post by linux phreak on 2008-05-06
Some thing like this has happened to me once.I tried to install pclinuxOs and in the process some thing got changed in my harddrive and during the boot screen it showed CHS instead of LBA for the harddrive.I wiped it clean but still during installation xp showed an error "cannot load operating system".Then i installed xubuntu and somehow it changed back to LBA and i was able to install XP again.I donot know what happened.But installing xubuntu saved me.

---

### Post by mdr on 2008-05-06
To my knowledge the fact that Gutsy and Hardy see your disks ok means that there is no HW failure as such,

Possibly it may be that they are SATA drives.  I believe XP (did) does not have native SATA drive support - you need to load an appropriate manufacturer sata driver for Windows from floppy for XP to see the disks.

For Vista - I would expect it to work but then I have never used it, Ubuntu from Warty for me.  XP/Vista cannot understand grub / linux partition / format info so that may be why that it is not seeing it.  Generally XP and previous can only install to the first disk found in bios.  However the fact that you used killdisk should negate that theory.
So that is a bit wierd. :confused:

I would get a sata driver and try and format the first disk as NTFS and see what happens.

As the others said when I dual boot Win32/XP and Ubuntu - I always install Windows first then Ubuntu and let grub do it's thing afterwards.

Hope this helps.
ps you should be able to change disk charateristics if needed in Bios if it has been changed from LBA to chs.

---

### Post by omns on 2008-05-06
What about installing Gutsy and XP like you used to do with success then deleting the Gutsy install during the Hardy install process

---

### Post by Dougie187 on 2008-05-06
Also, you might try using gparted to format a partition NTFS for your windows and see if the XP cd can pick that partition up. As with others, I agree with the "Install windows first, then ubuntu" idea. Thats what I alwasy do because windows boot loader f's up your ubuntu if you install it second.

---

### Post by sorfrena on 2008-05-06
Hi

I remembered I had a really similiar problem
I could install ubuntu over and over again but not windows xp.

You know why that happened?
My notebook is an asus...and like mine there are some notebooks that have something like a secret partition that they internally use, and I deleted it that time. This deletion did not affect ubuntu but affected xp.
Actually I don't remember what I did to make it work, but it was either formatting the entire partition or use the recovery cd of my notebook (call assistence for more info).

Any ways...I heard that ubuntu was giving some problems whith partitions, and I heard a guy saying that he solved the problem installing mandriva spring 2008. I suggest you to try this last one as first: get the cd of mandriva, install it: it will tell you bad things of your partition. Then after the installation has been completed, try to install windows xp. It could work in my opinion, I'd try it.

I hope someone can confirm or negate what I just said.
Hope to be of any help, good luck...I can remember how sucks not to have the partitions and the os you want.

---

### Post by phr0ze on 2008-05-06
The most logical answer is XP and VISTA don't have the driver for the disk controller. When you boot XP CD there is an option to hit F6 to load additional drivers. You need to find the drivers from the manufacturer website and use them when you boot. You may also want to google 'installing windows XP on BRAND MODEL' because if it is a driver issue, someone else will have a solution.

---

