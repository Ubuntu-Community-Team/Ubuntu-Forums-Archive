---
title: "Automatic firmware updates."
date: 2022-05-30
forum: New to Ubuntu
---

### Post by danielrjansen on 2022-05-30
I'm really new to ubuntu but I noticed yesterday that, upon boot, firmware updates wee being installed.
Is this normal default behavior? It seems less than wise considering the finality of bad firmware.

---

### Post by ActionParsnip on 2022-05-30
Firmware for what, please?

---

### Post by danielrjansen on 2022-05-30
bios, on a dell laptop. I didn't recognize it but it also looked like intel enterprise security stuff.

---

### Post by ActionParsnip on 2022-05-31
If you check /var/log/dpkg.log you may see the package it came from and so forth. Try grepping for "bios" or "Intel" or "firm". It may give clues.

---

### Post by danielrjansen on 2022-05-31
Thanks for your help, but my question was more along the lines of... is it normal to see firmware being installed during a system start when bios is loading? Does Ubuntu affect changes to hardware as a matter of course.

This was probably the third reboot (updates etc)

---

### Post by Holger_Gehrke on 2022-05-31
Are you talking about the package 'linux-firmware' (which was recently updated) ? This is firmware that gets loaded into various devices - wifi adapters, graphics card etc - during boot. It's not firmware for the PC itself.

Holger

---

### Post by #&amp;thj^% on 2022-05-31
> **danielrjansen said:**
> Thanks for your help, but my question was more along the lines of... is it normal to see firmware being installed during a system start when bios is loading? Does Ubuntu affect changes to hardware as a matter of course.

This was probably the third reboot (updates etc)

Please show this:
```
fwupdmgr refresh
Firmware metadata last refresh: 19 hours ago. Use --force to refresh again.
```
If there was a bios update, it would show during the boot, but you say/suggest it keeps happening on 3 reboots....this is not a normal behavior.
See if this reports anything we can use to help you:
```
sudo fwupdmgr clear-offline
 sudo fwupdmgr clear-history
```
Dells can be a bit finicky.
If all goes well, show this as well please:
```
fwupdmgr get-updates

```

---

### Post by GhX6GZMB on 2022-05-31
Linux, Ubuntu or any of the flavors will never update/change your BIOS. It's physically not possible.That Dell has built some online update mechanism into the BIOS is highly unlikely.
I think you're seeing a "linux-firmware" upgrade message, which you'll see on every upgrade.

---

### Post by #&amp;thj^% on 2022-05-31
> **ml9104 said:**
> Linux, Ubuntu or any of the flavors will never update/change your BIOS. It's physically not possible.

Dell

    If you are using UEFI and your F12 boot options include "Flash BIOS upgrade", one may download the BIOS upgrade .exe from Dell's website, and put it to your /boot/EFI/ folder. Reboot and select "Flash BIOS upgrade" option. In the dialog select the .exe file you have just downloaded and continue with the process.

    For more on Dell specific procedures, please see here. 
Source: [https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate)

---

### Post by oldfred on 2022-05-31
Linux now has fwupdate.
That does update UEFI for those systems that implement it.
My old Dell is not in the fwupdate (fwupd & fwupdmgr) database, but Dell did do updates from within Windows.
Dell was one of the first to support UEFI updates with fwupdate.

UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Since none of my systems are in the database, first thing I do is totally uninstall fwupdate files.

---

### Post by GhX6GZMB on 2022-05-31
> **1fallen said:**
> Dell

    If you are using UEFI and your F12 boot options include "Flash BIOS upgrade", one may download the BIOS upgrade .exe from Dell's website, and put it to your /boot/EFI/ folder. Reboot and select "Flash BIOS upgrade" option. In the dialog select the .exe file you have just downloaded and continue with the process.

    For more on Dell specific procedures, please see here. 
Source: [https://help.ubuntu.com/community/BIOSUpdate](https://help.ubuntu.com/community/BIOSUpdate)

Yes, fine. I'me aware of the intricacies with Dell.
But how on earth would Ubuntu run a .exe file? And the OP has not indicated that he/she has gone through such a dialog at all.

---

### Post by #&amp;thj^% on 2022-05-31
> **ml9104 said:**
> 
But how on earth would Ubuntu run a .exe file? And the OP has not indicated that he/she has gone through such a dialog at all.

It's not a .exe that ubuntu runs....just to save a debate you win...:KS
> **ml9104 said:**
> Yes, fine. I'me aware of the intricacies with Dell.

You used impossible for Linux, not accurate.
There are so many ways to do this..;)

---

### Post by danielrjansen on 2022-06-05
Hi, its not happening on every reboot but once on the third reboot. this makes sense because I just started using UEFI (installign distros with balenaEtcher) and have never applied updates to this laptop. 

Per instructions:
 
[B][FONT=courier new]fwupdmgr refresh

[COLOR=#000000]Updating lvfs[/COLOR]
Downloading&#8230;             [***************************************]
Successfully downloaded new metadata: 1 local device supported[/FONT][/B]

[FONT=monospace]Interesting that there is also an fwupdate in addition to fwupdmgr.

[/FONT][B][FONT=courier new]fwupdate  -L


[/FONT][/B][FONT=monospace][B][FONT=courier new][COLOR=#000000]failed: Error opening file /sys/firmware/efi/efivars/FWUPDATE_DEBUG_LOG-0abba7dc-e516-4167-bbf5-4d9d1c739416: No such file or directory

[/COLOR][/FONT][/B]If this is normal behavior that is fine. If I want to disable them I should do it in BIOS settings?

[/FONT]

---

### Post by VMC on 2022-06-05
> **Holger_Gehrke said:**
> Are you talking about the package 'linux-firmware' (which was recently updated) ? This is firmware that gets loaded into various devices - wifi adapters, graphics card etc - during boot. It's not firmware for the PC itself.

HolgerI suspect this is what the op is seeing, if its an auto update. Check time stamp on "/lib/firmware".

---

### Post by #&amp;thj^% on 2022-06-05
> **VMC said:**
> I suspect this is what the op is seeing, if its an auto update. Check time stamp on "/lib/firmware".

+1
3 agree on this> ;)

> **danielrjansen said:**
> ]If this is normal behavior that is fine. If I want to disable them I should do it in BIOS settings?


Yep Normal..
```
fwupdate -L
This program may only work correctly as root
failed: Error opening file /sys/firmware/efi/efivars/FWUPDATE_DEBUG_LOG-0abba7dc-e516-4167-bbf5-4d9d1c739416: No such file or directory

```

---

### Post by oldfred on 2022-06-05
The firmware file in Ubuntu is different than the fwupdate download of a new UEFI firmware.
Typically you want the latest of both, to avoid issues.
See post #10 on fwupdate.

You can disable the automatic update, but then should regularly do a manual update to prevent UEFI type virus.
While most of the fixes for this have been applied to both UEFI & kernel, some new virus get released and then another update is required.
Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching. 

My system is older and does not support fwupdate, so I totally uninstall it.
sudo apt-get purge fwupd

---

### Post by danielrjansen on 2022-06-05
It did say BIOS update. then it did some additional updates. It did another bios update today actually.

But if I understand correctly, its normal and fine and I should not change anything.

---

### Post by oldfred on 2022-06-05
My systems are older and I had to do manual updates.

But every update reset many UEFI settings to defaults.
Older Asus system had multiple settings I had to redo.
Newer Gigabyte system did not need many settings.
Each vendors UEFI is different, so best to check that your settings are correct.

---

