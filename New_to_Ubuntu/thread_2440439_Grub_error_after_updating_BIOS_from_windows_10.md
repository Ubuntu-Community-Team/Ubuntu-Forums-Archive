---
title: "Grub error after updating BIOS from windows 10"
date: 2020-04-10
forum: New to Ubuntu
---

### Post by negredol on 2020-04-10
I managed to create a dual boot laptop (ideapad C340) with windows 10 and ubuntu. Everything worked just fine until windows started to urge me to update BIOS. After naively doing so, computer kept booting directly into windows. After getting into BIOS and putting ubuntu above the Windows Boot Manager in the boot/ EFI menu I was able to get into the usual GNU GRUB menu after startup but after choosing ubuntu I received an error "initramfs unpacking failed: Decoding failed".

 I tried to fix Ubuntu via installation drive but it didn't seem to notice the existing version and proceeded with normal installation process onto USB drive. Neither does the linux partition show up when running command »sudo fdisk –l« (there only seems to be one Disk/dev/sda disc) in try ubuntu mode. However before booting in try Ubuntu mode, a slow “disk check” is performed followed by notification “Check finished: error found in 1 files! You might encounter errors.”
I am completely lost. I presume that a simple bios update couldn’t just destroy the os and erase everything? The ubuntu partition in windows 10 partition manager is still there but is supposedly empty (which is not unusual?).
I would very much appreciate any help. Since I am a beginner am a bit cautious so I don't ruin my access to windows.

---

### Post by oldfred on 2020-04-10
UEFI update resets some settings back to defaults.
I had to keep a list & redo them.

Windows updates turns fast start up back on and makes Windows first in boot order.
Major grub updates will also make Ubuntu/grub first in boot order so that is normal.
But you have to make sure Windows fast start up is off, otherwise Linux NTFS driver cannot see the NTFS partitions.

If you have an old BIOS install of Windows 10 from upgrade of Windows 7, then it is worse as Windows has a bug (they probably internally call it a feature) that "forgets" to write logical Linux partitions back into partition table. Data is still there & you then just have to restore entry in partition table, but if you overwrote that, then data is probably gone & best to just reinstall & restore from your backup.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by negredol on 2020-04-10
Thank you very much for your prompt repy. 

I used the ppa version with my live installer. However when installing boot-repair I received two errors:
```

...
saving system state
ERROR couldn't save system state: Current machine isn't Zsys, nothing to create
...
ERROR "update-grub" returned an error: exit status 1

```
Afterwards I managed to run boot-repair nonetheless. Here's the boot-info summary report: [https://paste.ubuntu.com/p/f8p2H8H8FZ/](https://paste.ubuntu.com/p/f8p2H8H8FZ/) , there was no auto-fix option. Again, it looks like only my installation drive appears. Should I try with boot-repair USB?

I have fast startup disabled in windows 10 and also tried disabling secure boot in UEFI.

---

### Post by oldfred on 2020-04-10
You are showing no drive, just the flash drive??

Do you see a drive in UEFI settings (not boot menu). And is it enabled and set to AHCI?
Windows may need AHCI drivers if you did not install those before, or it will not  boot.

You only show the UEFI boot entries for both Windows & Ubuntu. And a Linpus Lite.

---

### Post by negredol on 2020-04-10
Thank you so much. Apparently the UEFI update changed the controller mode from AHCI to RAID and I just had to change it back. I needed some courage to ignore the warning that [COLOR=#1A1A1B][FONT=&quot]"all existing data stored on the drivers will be erase when resetting Controller mode" but now everything works again. [/FONT][/COLOR]

---

