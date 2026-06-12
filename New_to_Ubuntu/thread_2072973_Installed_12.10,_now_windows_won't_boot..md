---
title: "Installed 12.10, now windows won't boot."
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Silman on 2012-10-18
Hello, 

this is my first time installing ubuntu on my home machine as i have ever only used ubuntu on my universities computers.. My computer is a laptop with two hard drives in RAID 0 and i think that is why i was lost when trying to install it, because the partitions instead of looking like /dev/sda/ looked like /dev/mapper/<a whole bunch of stuff>

Anyway, through lots of struggling i installed ubuntu onto about 80 gigs of unallocated space, but when i tried to install GRUB it wouldnt install so i used the boot repair that i got by installing
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair
```and it installed GRUB for me to /dev/mapper/<something ending in 'volume0'

When i boot it up i get the GRUB with these options

Ubuntu
Ubuntu Advanced Features (for recovery)
Windows Recovery (with some stuff about /dev/mapper/<volume ending in p2>)
Windows (with some stuff about /dev/mapper/<volume ending in p3>)
Windows (with some stuff about /dev/mapper/<volume ending in p4>)

I can take a picture and upload it because that wasn't very desriptive but in any case i know that the windows OS is on the volume ending in p4 because when i was in the partition manager that had the same allocated space as my windows install (about 800GB). But when i hit enter on the p4 volume it tells me "A disk read error occured Press cntl+alt+del to restart) and worse is cntrl alt del doesnt do anything! I was reading online about how i may have meessed up my MBR by installing GRUB. when i go into recovery mode and select "repair" it doesn't list a windows 7 install. So i don't know what to do to fix this! The good thing is that my data is all accessible through ubuntu (which installs and boots correcty) so i can back up my data.

What are your guys' suggestions?

---

### Post by oldfred on 2012-10-18
I do not know RAID, but post the link that running BootInfo from Boot repair creates as it details your system.

Windows normally installs to two partitions. A hidden boot/repair partition of 100MB and the main or c: drive partition. Your actual boot probably is the partition 3. Boot Repair often copies boot files from the boot partition to the main partition more as a backup as so many users do not know about the boot partition and just delete it or overwrite it thinking it is a boot partition for Ubuntu (it is not).

---

### Post by Silman on 2012-10-18
> **oldfred said:**
> I do not know RAID, but post the link that running BootInfo from Boot repair creates as it details your system.

Windows normally installs to two partitions. A hidden boot/repair partition of 100MB and the main or c: drive partition. Your actual boot probably is the partition 3. Boot Repair often copies boot files from the boot partition to the main partition more as a backup as so many users do not know about the boot partition and just delete it or overwrite it thinking it is a boot partition for Ubuntu (it is not).

This is the pastebin like that the boot repair gave to me after it said it was finished installing GRUB 2: [http://paste.ubuntu.com/1287978/](http://paste.ubuntu.com/1287978/)

I think that is what you were referring to, if not please let me know how to get you the information you are looking for.

EDIT: also what i mean when i say that the windows 7 repair doesn't list a windows 7 os installed i mean that [the window on the page here]("http://pcsupport.about.com/od/toolsofthetrade/ss/windows-7-startup-repair_6.htm") has nothing under its list of operating systems.

EDIT: Also Boot Repair had given this error/warning thing when i tried to repair my raid array:

Embedding-error-in-mapper/isw_cgeihheabf_Volume0 detected. You may want to retry after activating the [Separate /boot partition:] option.

---

### Post by oldfred on 2012-10-18
Some of the tools the script use need RAID tools installed and working. 

sudo apt-get install mdadm

I do not know enough on how RAID is configured. But grub will not install to a MBR if the first partition is too close to the start of a drive nor will it install to a partition boot sector. In may install if just enough room for conversion to blocklists or hard coded addresses. I do not fully know details but grub searches for its files. Blocks then do not have code to search but just a list of where the file is on the drive. That is unreliable as file may mobe on update or even fsck. 

So so you not have many sectors between start of RAID and first partition?

With MBR XP & older Linux started at sector 63 leaving sectors 1 thru 62 for core image. New systems since Vista and newer  Linux start first partition at sector 2048 for better use with newer 4K and SSD type drives. 

Part of the issue may be this also.

```
/dev/mapper/isw_cgeihheabf_Volume04   *     20,690,944 1,789,691,903 1,769,000,960  42 SFS


```

I do not know how you have RAID and SFS or dynamic partitions. Linux does not work with dynamic partitions as that is Windows proprietary.

---

