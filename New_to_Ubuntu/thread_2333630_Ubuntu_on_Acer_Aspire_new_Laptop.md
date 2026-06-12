---
title: "Ubuntu on Acer Aspire new Laptop ?"
date: 2016-08-11
forum: New to Ubuntu
---

### Post by peter.rollason on 2016-08-11
So the hard drive has gone and failed on my win 8 - upgraded to win 10 laptop !

I really can't be bothered to download win 8 core - activate the license through the bios then upgrade to win 10....

Ive installed Lubuntu\Ubuntu onto older older desktops and like what I saw - how easy would it be to install ubuntu onto a modern laptop such as my acer aspire E15 ? - Or just end up in a massive driver hunt ?

---

### Post by QIII on 2016-08-11
Hello!

I haven't looked specifically at your machine's specs, but in general - with few exceptions - all the drivers you need will be included in the kernel at install time.  There are some issues with specific ethernet adapters and such.  But those are few.

The driver scramble from the early days is gone.

---

### Post by oldfred on 2016-08-11
Acer has a unique requirement of setting a supervisor password in UEFI and then enabling "trust" on the .efi files in the ESP - efi system partition.
Some older threads may mention downgrading UEFI. But newer ones say newest UEFI works, so make sure you have newest UEFI from Acer.

       Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757
[/URL]
 Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062) 
      
 [http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/) 
    [URL="http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757"]
[/URL]

---

### Post by Geoffrey_Arndt on 2016-08-11
What "massive driver hunt"? . . . you have an all Intel machine (I3 & integrated Intel graphics).   Intel is very Linux friendly - - they've made a ton of money from selling Linux supported chips.   There are 3 distinct wireless chipsets for the Acer Aspire E15.    Intel, Atheros, and Broadcom.    So, if Intel - just as with graphics chipset, the driver/module is already in the Linux kernel.   If Atheros or Broadcom . . about a 75% chance the drivers are obtainable via one mouseclick from the Additional Drivers Utility in Ubuntu (just use dash to search "additional drivers").   

If by a long shot, you have a Windows only wireless chipset, then you go to Amazon and for about $10 usd - you get the Panda Ultra 150 b/g/n wireless nano size adapter.  Plug it in, . . . and you have wireless via realtek.   Works great.  (I have a couple dozen various wireless adapters that are all plug & play in Ubuntu).    Priced between $10 and $30 usd.

Biggest issue is as Fred writes - - may have to do the text file mods that are listed in his links.  Very doable.

---

