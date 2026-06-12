---
title: "no bootable device found, boot failed"
date: 2017-03-09
forum: New to Ubuntu
---

### Post by bniblet on 2017-03-09
Hi!

I've been fighting with this all day and have gotten nowhere.

This morning I woke to a grub command line when I turned on my Ubuntu 14.04.2 LTS laden Acer computer. Long story short, I reinstalled the same OS from a live USB (erase disk and install) and now I get a blue rectangle which tells me no bootable device is found or boot failed. if I hit esc I get the grub line, enter gets me to one choice; shimx86.efi which sends me back to the rectangle when I choose it. I have tried boot-repair tool which doesn't fix the problem but generates a paste file URL. Tried remounting the ESP using grub. Searched through various forums, found other threads about similar problems, but none of what was suggested worked for me. I tried reinstalling again not too long ago, still have the same error, and ran the boot-repair again so might as well put the most recent URL here [http://paste.ubuntu.com/24147767/d](http://paste.ubuntu.com/24147767/d) 

Hopefully someone can help. Thanks for reading this far! :P

---

### Post by bniblet on 2017-03-09
for some reason a /d was added to my paste URL here it is hopefully without it: [http://paste.ubuntu.com/24147767/](http://paste.ubuntu.com/24147767/)

---

### Post by bniblet on 2017-03-09
Hi again

I tried reinstalling (again erase disk and install) except this time I disabled 'secure boot'. Still a blue rectangle, slightly different message which I didn't write down, this time no grub prompt on hitting esc. I ran boot-repair again which got me back to the same no bootable device found, boot failed error. I suppose I would get the grub prompt again now that I ran the tool? Anyway here is the new pastebin thingy: [http://paste.ubuntu.com/24148264](http://paste.ubuntu.com/24148264) sorry to keep posting on my own thread but don't want to leave anyone with a misleading old link. Thanks to anyone out there who reads this and hopefully someone can help!

---

### Post by oldfred on 2017-03-09
All Acer have an unique requirement of setting an UEFI password (never lose that or immediately erase it) and then enabling "trust" on the ubuntu/grub .efi boot files.
Also make sure you have latest UEFI from Acer.
Some older threads mention downgrading to older UEFI, but newer threads say newest works.

Basically all the same, some just explain process better than others.
 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141) 

      
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)

---

