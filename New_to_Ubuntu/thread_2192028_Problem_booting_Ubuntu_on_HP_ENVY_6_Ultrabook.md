---
title: "Problem booting Ubuntu on HP ENVY 6 Ultrabook"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by dshng.junaid01 on 2013-12-05
Hi,
I bought this laptop a couple months and have been using Windows 8 on since. It got a 500 GB SATA and a 32GB SSD. I had my windows on the SSD and tried installing Ubuntu 13.10 from a live USB in the SATA. It all went well, no errors but it won't boot. The windows would just start up without giving me a chance to choose to boot Ubuntu. I read around various sources I cannot quote because I don't have em anymore and tried using boot-repair but it'd always(still does) give me the same error. Something about enabling sources in the sda6(the partition I installed Ubuntu in) that contain grub2. But I can't even boot it. So I tried adding Ubuntu in windows boot loader. I once again read at some various sources and used EasyBCD to add a ubuntu entry with grub2. I rebooted and the bootloader now had two entries. Linux and Ubuntu. Both brought me to grub2 command line where commands like linux and chainloader were all broken(didn't work).

So I deleted the windows partition from the SSD, I tried installing Ubuntu in the SSD. I tried installing grub in the SSD instead and ubuntu in the SATA and vice versa. I basically tried everything I could and still got the same error. I now have no OS and am using the live USB. I tried making a EFI partition of around 350 mb in start of my SATA but that didn't work either. Any help would be appreciated. Thanks.

p.s. Oh, and both my SSD and SATA got msdos partition table.

---

### Post by oldfred on 2013-12-05
Windows 8 pre-installed is UEFI and has gpt partitioning. Windows only boots with UEFI from gpt drives.
Ubuntu will install to gpt drives with UEFI boot or BIOS boot modes.
Both Windows and Ubuntu only boot from MBR(msdos) partitioned drives with BIOS mode.

If you converted gpt drive to MBR, did you also erase backup partition tables? If not you need to use fixparts to delete extra gpt data.
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If you want UEFI as boot mode which has some advantages, but is new and less well documented, you need to change to gpt partitioning.

You can run Boot-Repair from you Ubuntu install flash drive, but need to boot installer in correct boot mode. How you boot installer is how it installs.

      
 HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

