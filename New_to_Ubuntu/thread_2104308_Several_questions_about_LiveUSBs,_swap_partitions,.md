---
title: "Several questions about LiveUSBs, swap partitions, and loading to RAM."
date: 2013-01-12
forum: New to Ubuntu
---

### Post by Cyber Akuma on 2013-01-12
I want to install (not just put the LiveCD iso on a bootable USB with a persistent partition, but actually install) Ubuntu on a USB flashdrive so it can be updated and everything as if it was installed to an internal HDD.

First of all, I want to know if this would make any changes whatsoever to the Windows bootloader already on the system, I don't want the installer to touch the harddrives, only the flashdrive.

Also, I am not too familiar with how swap/paging works on Ubuntu. I know that on Windows, no matter how much RAM you have disabling it is a bad idea since many applications are hard-coded to use it, but is it the same for Ubuntu? Since the system has a very large amount of RAM and I don't want temp files to wear down the flash drive, is it safe to disable the swap partition and any other ram-based temp files during install? And if so, how?

Finally, I also read that the LiveCD supports a "toram" optional function, in which the disk gets loaded in it's entirety into RAM so you don't need it anymore to use the rest of the LiveCD until you reboot. Can you still do such a thing if Ubuntu has been installed to USB instead of running off USB as if its a LiveCD? Considering the OS seems to be under a gig, and reading a gig from a flashdrive shouldn't take too long, and I have a lot of RAM, I'd rather have the OS load into the RAM on boot than perform much slower on the USB drive.... but would I still be able to save updates, configuration changes, etc to the flashdrive so they will be there next reboot if I do this (if you even can on an installed version of Ubuntu)?

---

### Post by mapes12 on 2013-01-12
Having Ubu on a USB stick indicates that you need it to be transferable between machines. Is this correct or are you only looking to run it from the same machine?

---

### Post by Paqman on 2013-01-12
> **Cyber Akuma said:**
> 
First of all, I want to know if this would make any changes whatsoever to the Windows bootloader already on the system, I don't want the installer to touch the harddrives, only the flashdrive.


During the install you can choose where you want to install the Grub bootloader. If you choose to install it to your USB stick instead of the hard drive then Windows will be untouched. This is in fact the correct way to set up a USB-stick based system, as you don't want the bootloader to get horribly confused when you boot without the USB present.

> Also, I am not too familiar with how swap/paging works on Ubuntu. I know that on Windows, no matter how much RAM you have disabling it is a bad idea since many applications are hard-coded to use it, but is it the same for Ubuntu? Since the system has a very large amount of RAM and I don't want temp files to wear down the flash drive, is it safe to disable the swap partition and any other ram-based temp files during install? And if so, how?

You can [adjust the "swappiness" of your system]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F"), all the way down to zero if you want. This will minimise the amount of swapping. If you have plenty of RAM you could also run without any swap, I haven't tried it myself but others report it works fine.

> 
Finally, I also read that the LiveCD supports a "toram" optional function, in which the disk gets loaded in it's entirety into RAM so you don't need it anymore to use the rest of the LiveCD until you reboot. Can you still do such a thing if Ubuntu has been installed to USB instead of running off USB as if its a LiveCD? Considering the OS seems to be under a gig, and reading a gig from a flashdrive shouldn't take too long, and I have a lot of RAM, I'd rather have the OS load into the RAM on boot than perform much slower on the USB drive.... but would I still be able to save updates, configuration changes, etc to the flashdrive so they will be there next reboot if I do this (if you even can on an installed version of Ubuntu)?

If this is what you want you may want to look at one of the distros designed specifically to do this, such as [Puppy Linux]("http://www.puppylinux.com/"). IIRC Puppy can save any changes made while running on a ramdisk on shutdown. I believe it will also do write caching to reduce wear on USB sticks, which is middle-of-the road option.

---

### Post by Cyber Akuma on 2013-01-13
> **mapes12 said:**
> Having Ubu on a USB stick indicates that you need it to be transferable between machines. Is this correct or are you only looking to run it from the same machine?

While it would be nice to use it across different systems it will most likely only be used on the same one.

> **Paqman said:**
> You can [adjust the "swappiness" of your system]("https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F"), all the way down to zero if you want. This will minimise the amount of swapping. If you have plenty of RAM you could also run without any swap, I haven't tried it myself but others report it works fine.

If I tell it not to install a swap partition at all when manually defining partition sizes during the install do I still need to mess with this value? Will it create a swap file instead if I choose to not use a swap partition, or just disable swap?


> **Paqman said:**
> If this is what you want you may want to look at one of the distros designed specifically to do this, such as [Puppy Linux]("http://www.puppylinux.com/"). IIRC Puppy can save any changes made while running on a ramdisk on shutdown. I believe it will also do write caching to reduce wear on USB sticks, which is middle-of-the road option.

I am aware of Puppy Linux, used it on some real old systems before, I was looking to specifically use Ubuntu for this one though.

-----------

By the way, I forgot to ask. If your hardware supports it, do you have any idea of Ubuntu supports TRIM over RAID0? Especially on NTFS if the filesystem makes any difference?

---

### Post by Cheesemill on 2013-01-13
> **Cyber Akuma said:**
> If I tell it not to install a swap partition at all when manually defining partition sizes during the install do I still need to mess with this value? Will it create a swap file instead if I choose to not use a swap partition, or just disable swap?
If you install without specifying a swap partition the system wont create anything, your system will run without any swap at all.
> Finally, I also read that the LiveCD supports a "toram" optional  function, in which the disk gets loaded in it's entirety into RAM so you  don't need it anymore to use the rest of the LiveCD until you reboot.  Can you still do such a thing if Ubuntu has been installed to USB  instead of running off USB as if its a LiveCD? Considering the OS seems  to be under a gig, and reading a gig from a flashdrive shouldn't take  too long, and I have a lot of RAM, I'd rather have the OS load into the  RAM on boot than perform much slower on the USB drive.... but would I  still be able to save updates, configuration changes, etc to the  flashdrive so they will be there next reboot if I do this (if you even  can on an installed version of Ubuntu)?A Live CD may take up under a GB but this isn't the same with an installed system. A basic full installation uses around 4GB of space so it isn't really feasible to load the entire OS into RAM.Also because of the way the Linux kernel handles memory caching then a program is only loaded from the flash drive into memory the first time you use it. Even if you close an application it will stay cached in memory (if it's availible) so the next load will be much quicker. Running the whole OS from RAM still means loading everything from the stick once anyway, so you aren't really gaining any advantage by doing what you suggest.

---

### Post by black veils on 2013-01-13
its not just swapping which causes excessive read/write for a usb stick. i think i have seen posts with details on how to tweak it appropriately.

regardless of tweaking, you might struggle with slowness of system running from usb stick, better to use either Xubuntu or Lubuntu. unless its a usb 3.0, in which case there may not be a considerable issue.

---

### Post by oldfred on 2013-01-13
If you have a lot of RAM full Ubuntu runs ok, not speed. The lighter weight versions will load quicker, but writes to flash are usually the slowest part. Even though I only have USB2 ports my newest flash drive is USB3 which is supposed to be a bit better.

You have to use manual install, to get the option on where to install the grub2 boot loader. And you want grub installed to flash drive not internal drive.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

    Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

    If you want full encryption, it is a bit more complex as you have to have LVM with alternative installer. But they have discontinued alternative installer with 12.10. 
       Ubuntu Encrypted Flash Memory Installation using alternative text based installer, if you do not want encryption you just use standard Desktop installer. 
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

HOW TO Install Lubuntu on USB Drive - amjjawad
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

       With SSD or Flash drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

