---
title: "Booting in emergency mode"
date: 2016-10-20
forum: New to Ubuntu
---

### Post by annadg on 2016-10-20
Hi,

I'm still quite new to Ubuntu and Linux. I successfully installed a dual boot between Ubuntu 16.04 and Windows 10 about a month ago. Ever since my laptop ran out of battery yesterday however, Ubuntu will only go into emergency mode after booting (GRUB still works). 

I have made a backup using a live USB and tried to look for a solution on this forum, but I haven't found anything that helps/that I can fully understand. In the output from typing in journalctl -xb, the following is marked red: "Failed to create swap unit file /run/systemd/generator/dev-mapper-isw_bbfhiejded_ASUS_OS9.swap, as it already exists. Duplicate entry in /etc/fstab?"

How should I go about fixing this error?

Thanks!

---

### Post by oldfred on 2016-10-20
Mapper indicates either BIOS or FakeRAID, or Linux LVM?

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by colmax on 2016-10-20
When it asks to duplicate entry maybe press y then enter and see if that helps
Seems linux can't find or write to your swap partition (which is a part of the disk that is used similar to ram)
May need to reformat the swap partition
Cheers

---

### Post by annadg on 2016-10-20
Here's the link from boot info: [http://paste2.org/kWggWXfz](http://paste2.org/kWggWXfz)

I should probably have added that my laptop has 2 SSDs in RAID 0 configuration (set up by the manufacturer), which caused earlier Ubuntu versions to fail to install.

---

### Post by colmax on 2016-10-20
Think Oldfred was right on the ball
Seems you're running Fakeraid which is motherboard support i think
Some raid software is not supported by ubuntu yet
Raid0 is striping methinks which makes multiple disks seem 1 block/volume with some redundancy
Your motherboard is probably saying it's 1 volume and linux is seeing 2 (hda, hdb)
Swap may need to be on the same actual drive as your ext4 partition
Gotta admit this is a bit outside of my knowledge
Cheers

---

### Post by oldfred on 2016-10-21
You have at least a couple of issues that everyone has.
You left Windows with fast start up on, which is always on hibernation. That must be off.
And it looks like UEFI Secure boot is on. Many systems works better with that added complication off for now.

But then you have RAID 0. Which was used by some to speed older hard drives where needing faster drive response. But never for a use where data may be actually saved onto drive. With SSD, you get most of speed increase with just SSD.
       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

Some with dual RAID, turn RAID off. If RAID 1, it usually just works, but RAID 0 has half of data on one drive and half on other drive. So you can only do that with full backups. With RAID 0 you should have full backups and a very regular basis as you are trading speed for reliability.

Several older threads, with RAID 0 systems.
       
 MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[URL="http://ubuntuforums.org/showthread.php?t=2297815"]http://ubuntuforums.org/showthread.php?t=2297815
[/URL]
 Sony Vaio  - EFI dualboot Ubuntu 12.04 and Windows 8 in Raid 0 
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/) 
      
 acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043) 
    [URL="http://ubuntuforums.org/showthread.php?t=2297815"]
[/URL]

---

### Post by annadg on 2016-10-21
Thanks for your replies! I turned off secure boot, fast start up was already turned off in my windows settings. Then formatted the swap partition and tried to reinstall, but I got the exact same error on booting.

RAID 0 is a factory config, but I'm reluctant to turn it off as I enjoy the speed for running simulations and models. I am aware of the pros/cons of RAID 0 and create backups regularly. I will look into the threads you sent more carefully.

---

