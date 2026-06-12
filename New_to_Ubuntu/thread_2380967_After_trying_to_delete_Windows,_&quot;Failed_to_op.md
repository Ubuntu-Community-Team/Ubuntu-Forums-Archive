---
title: "After trying to delete Windows, &quot;Failed to open \EFI\BOOT\grubx64.efi - Not Found&quot;"
date: 2017-12-24
forum: New to Ubuntu
---

### Post by leo.soaivan on 2017-12-24
Happy Holidays all,

Over the past 24 hours I've been trying to get an SSD up and running with only Ubuntu on a Samsung NP-QX411-W01US. I started with a Windows 10 dual-boot about two years ago on an HDD, and just recently decided to get rid of Windows. 

Unfortunately, I've created more issues than I can effectively troubleshoot. I believe the issues may have begun when I tried deleting the Windows partition in the old HDD using gparted.

I've tried disk erases with full installs. I've also tried "Something Else" with custom partitions, including one with an EFI System Partition, as recommended by boot-repair. The output is here: [https://paste.ubuntu.com/26245908/](https://paste.ubuntu.com/26245908/)

The errors I'm getting at this point are as follows:[INDENT]Failed to open \EFI\BOOT\grubx64.efi - Not Found
Failed to load page image \EFI\BOOT\grubx64.efi : Not Found
start_image() returned Not Found
[/INDENT]

At this point, without the LiveUSB inserted, the screen just flickers black in a loop.

After some research, it seems that perhaps I need to look into GPT partitioning? My understanding of all of this is pretty limited, so any assistance would be greatly appreciated.[URL="https://paste.ubuntu.com/26245908/"]

[/URL]

---

### Post by oldfred on 2017-12-24
Have you tried with UEFI Secure Boot off?
Boot-Repair says it may be on.

What brand/model system? Some require work arounds.

You show ESP and mount of that ESP in your fstab, so configured for UEFI boot. And you are using gpt partitioning.

You do have an older grub installer to gpt's protective MBR, just do not boot in CSM/BIOS/Legacy  boot mode.

---

