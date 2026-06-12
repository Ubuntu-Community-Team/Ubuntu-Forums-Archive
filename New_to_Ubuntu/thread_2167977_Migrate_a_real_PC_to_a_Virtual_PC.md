---
title: "Migrate a real PC to a Virtual PC"
date: 2013-08-15
forum: New to Ubuntu
---

### Post by superthin on 2013-08-15
Hello everybody,

My department bought me a new laptop. I have to give them old PC next some few days. So, I want to migrate all OS, data,... (exactly: a 500GB HDD) from old PC to a VirtualBox VDI file 

I installed Ubuntu 13.04 to the laptop, and VirtualBox installed also. I don't want to install everything to the laptop from beginning... So, I determine I will use virtual PC inside real laptop. I don't think BSOD with Win 7 in or problems with Ubuntu 12.10 from old HDD because I sysprep(ed), and Ubuntu can be installed and remount /home.

**Details:**

This is my partitions:

[IMG]http://i.imgur.com/O1Tqkkg.png[/IMG]

After Clonezilla the HDD to an portable Western HDD, a list file:

```

    total 383132363
    drwx------ 1 superthin superthin        4096 Th08 15 19:49 .
    drwx------ 1 superthin superthin        4096 Th08 15 19:47 ..
    -rw------- 1 superthin superthin         769 Th08 15 17:01 blkdev.list
    -rw------- 1 superthin superthin        5985 Th08 15 19:49 clonezilla-img
    -rw------- 1 superthin superthin           4 Th08 15 19:47 disk
    -rw------- 1 superthin superthin       21639 Th08 15 19:47 Info-dmi.txt
    -rw------- 1 superthin superthin       22465 Th08 15 19:47 Info-lshw.txt
    -rw------- 1 superthin superthin        2226 Th08 15 19:47 Info-lspci.txt
    -rw------- 1 superthin superthin         170 Th08 15 19:47 Info-packages.txt
    -rw------- 1 superthin superthin         112 Th08 15 19:49 Info-saved-by-cmd.txt
    -rw------- 1 superthin superthin          20 Th08 15 19:47 parts
    -rw------- 1 superthin superthin          33 Th08 15 17:01 sda1.info
    -rw------- 1 superthin superthin    32116493 Th08 15 17:01 sda1.ntfs-img.aa
    -rw------- 1 superthin superthin          33 Th08 15 17:15 sda2.info
    -rw------- 1 superthin superthin 32339521753 Th08 15 17:15 sda2.ntfs-img.aa
    -rw------- 1 superthin superthin 34359738368 Th08 15 17:30 sda3.ntfs-img.aa
    -rw------- 1 superthin superthin 34359738368 Th08 15 17:44 sda3.ntfs-img.ab
    -rw------- 1 superthin superthin 34359738368 Th08 15 17:59 sda3.ntfs-img.ac
    -rw------- 1 superthin superthin 34359738368 Th08 15 18:13 sda3.ntfs-img.ad
    -rw------- 1 superthin superthin 34359738368 Th08 15 18:28 sda3.ntfs-img.ae
    -rw------- 1 superthin superthin 12282617582 Th08 15 18:33 sda3.ntfs-img.af
    -rw------- 1 superthin superthin 34359738368 Th08 15 18:47 sda5.dd-img.aa
    -rw------- 1 superthin superthin 34359738368 Th08 15 19:02 sda5.dd-img.ab
    -rw------- 1 superthin superthin 34359738368 Th08 15 19:16 sda5.dd-img.ac
    -rw------- 1 superthin superthin 34359738368 Th08 15 19:31 sda5.dd-img.ad
    -rw------- 1 superthin superthin 34359738368 Th08 15 19:45 sda5.dd-img.ae
    -rw------- 1 superthin superthin  4074766336 Th08 15 19:47 sda5.dd-img.af
    -rw------- 1 superthin superthin          37 Th08 15 17:01 sda-chs.sf
    -rw------- 1 superthin superthin     1048064 Th08 15 17:01 sda-hidden-data-after-mbr
    -rw------- 1 superthin superthin         512 Th08 15 17:01 sda-mbr
    -rw------- 1 superthin superthin         579 Th08 15 17:01 sda-pt.parted
    -rw------- 1 superthin superthin         490 Th08 15 17:01 sda-pt.parted.compact
    -rw------- 1 superthin superthin         361 Th08 15 17:01 sda-pt.sf
    -rw------- 1 superthin superthin          53 Th08 15 19:47 swappt-sda6.info

```

My question: the best way to convert all files above to a VirtualBox VDI file? Sorry for my English.

Thank you very much!

Best regards,
SuperThin

---

### Post by DuckHook on 2013-08-16
An ambitious and risky undertaking. It is much easier to migrate a Linux install the way you desire. It is also possible with Windows, but very difficult and very risky with a high possibility of hosing your Windows OS. The problem is that Windows is not designed to port onto different HW. In fact, it is designed to adhere to the HW it was initially installed on as an anti-piracy measure.

[Here]("https://www.virtualbox.org/wiki/Migrate_Windows") are the VirtualBox instructions for migrating a physical Windows installation to VirtualBox. Note that you must have a Windows licence for your new laptop to do this. More importantly, this is one of the highest risk projects that you could possibly attempt. I would estimate your chances of success to be far less than 50%. If these steps do not work, it is likely that you will corrupt your Windows installation to the point that it is unrecoverable. Therefore, make sure all of your critical Windows data is backed up so that you can create a new Windows VM the traditional way and be able to restore your data.

---

