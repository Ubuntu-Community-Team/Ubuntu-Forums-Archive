---
title: "I have 3 primary partition on my hard disk. Can i install ubuntu?"
date: 2013-08-24
forum: New to Ubuntu
---

### Post by vikashchandola26 on 2013-08-24
I have attached image of my disk management in attachment. 
I am thinking to install Ubuntu 12.04 in my computer with "install alongside windows" option(as it is shown one of three option during installation time). So how many primary partition does Ubuntu require for installation(as windows require two system and C, two). If it require one partition then it should work fine but if it require more than one then there may be some problem. So i want to know does "install alongside windows" option is a securemethod to install Ubuntu 12.04?

---

### Post by deadflowr on 2013-08-24
Ubuntu doesn't require a primary partition, only a single partition.
Unlike Windows, it can install completely in a logical partition.

---

### Post by oldfred on 2013-08-24
Ubuntu does like two partitions as a default / (root) and swap. But if you have a lot of RAM you may not need swap. But default installs almost always make swap a logical partition and root can be logical also. 

Also Ubuntu will not install in NTFS formatted partitions (unless wubi which is be discontinued but still available) and do not create partitions with Windows as instead of the extended partition as a container for an unlimited number of logical partitions it often converts to dynamic partitions which does not work with Linux.

---

### Post by JKyleOKC on 2013-08-24
Which version of Windows is on the machine? I ask because some Win7 systems and, so far as I know, all Win8 systems use UEFI to boot, and these systems are not limited to four primary partitions. However, they do lead to other puzzlements for the unwary. Once we know what's on your system already, we can give you more accurate advice. For now, if the system is "conventional" (the original MBR methods) the "install alongside windows" option should work -- but if it's a UEFI-based box, it would introduce lots of problems. Thus it's best to give us as much detail as you can, and wait for the replies.

---

### Post by vikashchandola26 on 2013-08-24
> **JKyleOKC said:**
> Which version of Windows is on the machine? I ask because some Win7 systems and, so far as I know, all Win8 systems use UEFI to boot, and these systems are not limited to four primary partitions. However, they do lead to other puzzlements for the unwary. Once we know what's on your system already, we can give you more accurate advice. For now, if the system is "conventional" (the original MBR methods) the "install alongside windows" option should work -- but if it's a UEFI-based box, it would introduce lots of problems. Thus it's best to give us as much detail as you can, and wait for the replies.
it's windows 7 home basic...
laptop model number is HP pavillion g6 2016tx

---

### Post by JKyleOKC on 2013-08-24
I have an HP Pavilion with Win7 home basic on it, also, but cannot find its exact model number at the moment since I'm on a different machine and cannot reach the Win7 partition of the HP from this box. My HP **does** have UEFI on it, which is where I learned about the problems it can cause. Check out the links in OldFred's message above to find out how you can test your system to tell whether it's UEFI or not.

Incidentally, it was OldFred who walked me through the maze of getting set up properly via UEFI. One of the problems is that the Live CD doesn't automatically detect it, but both Windows and Ubuntu have to be using the same boot technique. He can help you through the maze, also, if it turns out that you do have a UEFI system. Avoid trying suggestions from others, at least until he has an opportunity to guide you...

A starting point, however, for any dual-boot installation is to use the Win7 disk management tools to first defragment your disk, then reduce the size of the System (C: ) partition as much as the tool will permit. In my case I could only free up about 250 GB of space for Linux, but that was enough for my needs. Once that's done, wait for suggestions from OldFred.

EDIT: I just checked Fred's link, and it doesn't seem to specifically address how to test and find out whether you have UEFI or BIOS in your machine. If you can load the Live CD and use the "Try" choice to get Ubuntu running, you can open a terminal box and type "sudo fdisk -l" (that's a lower-case L, not a numeral "1") to find out. If it's UEFI, the report will tell you that fdisk does not support GPT drives -- and a GPT drive implies use of UEFI.

However, Fred may have a simpler way to tell...

---

### Post by oldfred on 2013-08-24
You can copy & paste this into a terminal, but I think that is after you have installed and booting from live installer may not be correct.
 Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

I prefer to see partitions and if you have gpt partitioning not msdos (MBR) and have an efi partition then you have UEFI. If just the 100MB boot and main install you have BIOS.

sudo parted -l

---

### Post by vikashchandola26 on 2013-08-25
i think this uefi problem is not in with computer coz i have run ubuntu live many times as well as installed it once in past using wubi(older version of ubuntu)...

---

