---
title: "GRUB won't boot at start-up: Ubuntu 14.04 dual boot windows 8.1"
date: 2014-06-27
forum: New to Ubuntu
---

### Post by george54 on 2014-06-27
Hi everyone,

I have an Acer Aspire V5 with Windows 8.1 and recently installed Ubuntu 14.04 but I can't seem to get GRUB to start at the boot. I ran Boot Repair and got the following error with the log file:

- The boot files of [The OS now in use - Ubuntu 14.04 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

- [http://paste.ubuntu.com/7712941/](http://paste.ubuntu.com/7712941/)

I've installed the software updates too so I don't know what else I can do to have GRUB start on boot.

I don't know if this is helpful but when I go into the UEFI and select "Boot From a Device" I see Ubuntu there and consequently when I select it, the computer boots with GRUB. But when I restart, it goes back to Windows.

Can somebody please help me get GRUB to start on boot?

Thanks for the help!

---

### Post by Bucky Ball on 2014-06-27
Welcome. Did you install Ubuntu in UEFI? It appears to have missed putting in the, probably already existing, efi partition. 

If you boot from a Live DVD/USB, launch Gparted and have a look, do you see a small FAT partition there anywhere, <500Mb?

---

### Post by george54 on 2014-06-27
So went into Gparted and yes there is a small FAT32 partition there thats flagged with boot. So if it's there how do I make it start on boot?

Thanks a lot!!

---

### Post by Bucky Ball on 2014-06-28
Well, if you go into BIOS and switch off anything to do with Win8, e.g. fast start, fast boot, etc. (although this may not be necessary now with 14.04, best check) then make sure you install Ubuntu in EFI mode, choose 'Something Else' when you get the partitioning section of the install and manually set up your partitions, the install should identify that EFI partition and install accordingly. 

Main thing is Ubuntu needs to be installed in EFI if Windows is, and Win8 always is if it is pre-installed.

Other main point: Just create the partitions you are going to use (/, /swap, /home perhaps) when partitioning and LEAVE the existing partitions. Check they are set to 'Do Not Use' when you are there. Then should be fine.

---

### Post by george54 on 2014-06-28
I got it fixed...

I'd already switched off secure boot and fast boot prior to installing Ubuntu. And I did install my Ubuntu in EFI mode by choosing 'Something Else' and when I got to the partitioning section of the install I set up three manual partitions for Ubuntu. The first for /, the second for /home, and the third for swap. 

I restarted the computer after the installation and it went straight to Windows so I ran boot repair right afterwards. But it still booted into Windows so I ran [COLOR=#666666]*bcdedit /set "{bootmgr}" path \EFI\ubuntu\grubx64.efi*[/COLOR] in the Windows command prompt, but it still booted straight into Windows.

In the BIOS Ubuntu was not listed in the boot order options either. After many failed attempts I restarted from the Ubuntu live session and went straight into BIOS and there was Ubuntu staring at me in the boot order options. I don't know what I did but I guess it worked.

Thanks for the help.

---

### Post by Bucky Ball on 2014-06-28
Good news. Enjoy! ;)

---

