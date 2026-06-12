---
title: "UEFI Ubuntu installed alongside Win7"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by Steavio99 on 2012-11-25
I believe I have the same problem.

I had a working windows 7 installation on a 1 TB hard drive, and wanted to put ubuntu on it as well. I installed xubuntu (12.something, it was the most recent as of about 2 weeks ago) alongside windows, giving it 100gb of space. It did some weird partitioning (list provided later) but in short I believe it has installed successfully.

However, when I restart, my computer boots directly into windows. I attempted to fix this with ubuntu's boot-repair utility. No luck.

I did a little research, and I think I am most likely having one of these two problems.

1) GRUB is not installed on the MBR. I was not prompted about where I wanted to install GRUB.

2) The partitions containing grub/ubuntu are too far away from the start of the hard drive to be detected by my computer's BIOS.

While I have enough conceptual knowledge of computer-related things to understand it when people talk about computers, my working knowledge is rather small, so I'm not comfortable following a tutorial that has a high risk of me losing my windows installation. While I have a full backup of my windows system, I am a busy person and don't really have time to spend all day restoring it or doing a complete reinstall of both OS's.

I haven't found a simple guide for installing grub to the MBR (which seems like it should be a simple thing to do), and I'm dubious about trying to move the windows partition as that seems like there would be a high risk of data loss.

Can somebody provide me with a quick guide on how to install GRUB to the MBR or a link to a simple tutorial (or a tutorial to solve whatever you think my problem is, if you have a different diagnosis)?

Some more information:

1) Attachment screenshot from gparted.
2) I have a thumb drive with fedora 17 on it that I can use to run gparted (hence the screenshot) and commands from the terminal.
3) From ubuntu's boot-recovery tool, the troubleshooting file: paste2.org/p/2522097

---

### Post by Steavio99 on 2012-11-25
The full message:

> Boot successfully repaired. [It wasn't; I still have the same problem]

Please write on a paper the following URL:
[http://paste.ubuntu.com/1386669/](http://paste.ubuntu.com/1386669/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.


The  boot files of [Ubuntu 12.10] are far from the start of the disk. Your  BIOS may not detect them. You may want to retry after creating a /boot  partition (EXT4, >200MB, start of the disk). This can be performed  via tools such as gParted. Then select this partition via the [Separate  /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by oldfred on 2012-11-25
Moved to a new thread as your issue is totally different and answers get confusing when trying to suggest repairs for two different systems in one thread.

Did you install the 64 bit version on Ubuntu. 

You installed Ubuntu in legacy mode not UEFI but have Windows in UEFI. Both systems must be in same mode.

How you boot installer - UEFI or Legacy and RepairCD/USB is how it will work. 

Boot repair will convert a BIOS/Legacy install of 64 bit Ubuntu to UEFI by uninstalling grub-pc and installing grub-efi.

With UEFI you do not install grub to the MBR as that is not used, but install the grub boot loader to the efi partition. MBR only exists in gpt partitions so old tools see drive as used for gpt.

It also looks like you took boot flag off of FAT32 sda1 partition. It has to be there. Use gparted to add it again.
> 
       In GPT fdisk, ESPs have a type code of EF00. In libparted-based tools, you mark the ESP as such by setting its "boot flag." Note that the libparted "boot flag" means something entirely different under MBR, and you should not set the "boot flag" on any OS partition under GPT!

    

---

### Post by YannBuntu on 2012-11-26
Hello

> **Steavio99 said:**
> http://paste.ubuntu.com/1386669/

There was a bug in Boot-Repair that prevented your ESP detection. I just uploaded a fix.
Please wait ~1hour, then update Boot-Repair (boot-sav and boot-repair packages), then run the "Recommended repair" and tell us the new URL that will appear.

---

### Post by Backharlow on 2012-11-26
I just installed Mint (uses ubuntu installer) onto an HP installed Win7 with 4 partitions, like this one. In the windows 7 partition manager, I deleted the one labelled HP_TOOLS. It is just a bios update utility. 
I then shrunk C: (you can do that in win 7), and then installed Mint into free space between C: and RECOVERY. It works fine. No issue with grub. On that the table looks like:

| SYSTEM | C: | ext4 root | swap | RECOVERY |

SWAP and Root are an extended partition, IE they only count as 1 primary, since the drive can only have 4 primary partitions.
I had no issues with grub on boot.

---

