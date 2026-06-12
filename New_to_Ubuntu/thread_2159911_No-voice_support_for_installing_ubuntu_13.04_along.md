---
title: "No-voice support for installing ubuntu 13.04 alongside with windows 7 in ssd"
date: 2013-07-05
forum: New to Ubuntu
---

### Post by praseednair on 2013-07-05
Hello, I have tried to install ubuntu 13.04 alongside with my windows 7 in my 80gb SSD. The installer does not show my SSD for installation but only my 500gb HDD. When I press the option that small drive is hidden, I see my SSD and HDD partitions but I am not sure how to forward from here. Please advice.
[ATTACH=CONFIG]244420[/ATTACH]

---

### Post by Mark Phelps on 2013-07-05
Sorry, you don't have enough room on  the SSD to install Ubuntu.  You've only got about 10GB of free space inside the Win7 OS partition -- and Windows needs that space.  If you shrank it down to get 10GB for Ubuntu, you would cripple Win7 and it would likely not run anymore due to insufficient free space.

You would do better using a Windows partitioning tool to shrink down  E: to leave some room for Ubuntu.  30GB should be sufficient.

You can shrink E: using the Win7 Disk Management utility, or better yet, you can download the Minitool Partition Wizard Home edition, install that, and use it.

BEFORE you charge into dual-boot installation, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  This will prove invaluable if the Win7 boot loader gets corrupted as part of the dual-boot setup.

Once you have the space freed up, do the following:
1) Shut down the PC
2) Disconnect the SSD -- this is IMPORTANT
3) Insert the Ubuntu install media
4) Boot Ubuntu, use the Something Else option to create partitions and install to the HDD
5) Shut down the PC
6) Reconnect the SSD -- but continue to boot from the HDD
7) Boot into Ubuntu (should do this by default)
8) Open at terminal and enter "sudo update-grub".  This will regenerate the GRUB config file and add an entry for Windows
9) Reboot the PC -- you should now get a GRUB menu with entries for Ubuntu and Windows

---

### Post by dannyboy79 on 2013-07-05
you only have 28.5GB free on your SSD. Is there some stuff you could move off the SSD onto the 500GB drive to free up more space on the SSD (maybe any large files which are in your My Documents folder? If you really want Ubuntu on your SSD then I would leave at least 30GB for windows and minimum 15GB for Ubuntu.

As Mark suggested I would make a win7 backup disk AFTER you remove some of the large files taking up space on your C drive. 

The reason why the SSD may not be showing up is because win7 was installed via UEFI and or secure boot? However win7 was installed then you have to install ubuntu the same way as far as either old BIOS or UEFI

---

