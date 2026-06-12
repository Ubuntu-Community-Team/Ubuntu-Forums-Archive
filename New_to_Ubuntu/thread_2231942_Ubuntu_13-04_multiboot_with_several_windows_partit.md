---
title: "Ubuntu 13-04 multiboot with several windows partitions and versions"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by johnwerneken on 2014-06-28
Ubuntu 13-04 multiboot with several windows partitions and versions

Having followed various detailed tip sheets to install previous versions of Ubuntu in this system, which in penitent point focused on (1) installing grub in the Ext4 not the mbr and (2) credit to add the Linux entry to the windows bcd, I expected no issues, but had one: either 13.04 entry would no longer work, if 13.04 installed with grub in the Ext, or with grub in the mbr, no windows boot mgr. I did not know this was an exclusively windows issue at first, so I resolved it by letting grub run the multiboot.

However, only 13.04 and my two flavors of windows 8 booted not my win 7, so I disliked my solution.

Today (hung over and bored) I tried to switch the multi to windows bootmgr using bcdedit. 

OOOPS. No boot at all, no OS.

The win 8.1 DVD repair option gave a “connected device fail” sort of message, prolly referring to external drive(s) and SSD(s).

On reboot, windows bootmgr would load win8.1 current version. Unexpected considering the error message, but welcome.

THEN I used EasyBCD in windows to delete the only Linux entry and auto create a new one.

On next boot, both win 8’s and 13.04 worked but now not win7 – just as with grub running it.

Aha.

I edited the windows BCD in EasyBCD to set the win7 boot device to the win7 partition.

Lol it all works.

MY takeaway (ymmv) is: if Windows is the preferred bootmgr not grub or grub2, then use the windows GUI tools available (seems to be bullet proof with EasyBCD; have others here but did not try them) to fix issues, not bcdedit at windows shell. 

Or, when what once worked, as far as how to maybe extract the relevant first 512 count part of linux.bin for windows bootmgr to use no longer does, the web-updated tools (for either OS, win or unix) are a better choice, at least for me.

---

### Post by oldfred on 2014-06-29
Windows only boots from one partition set as boot flag on the drive set in BIOS as boot drive.
Windows literally moves all boot files from second installs to the one bootable (active) partition. 
So only one Windows partition is seen by grub as bootable.

You can separately install Windows to a second primary partition or a second drive by setting second drive as bootable in BIOS and adding boot flag to NTFS primary partition. Then that install also has boot files for grub to find.

       To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

    
Use EasyBCD forces grub to install its boot loader to a partition boot sector. Grub2's standard configuration is too large and it converts to block lists which are not recommended. If any file is updated and is at a different address on drive then you will have to reinstall grub to partition boot sector to fix it. Be sure to have your Live installer handy to reinstall grub. But not really a grub issue.

---

