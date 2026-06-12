---
title: "Ubuntu 14.04 won't boot properly"
date: 2014-09-23
forum: New to Ubuntu
---

### Post by CJ_Hudson on 2014-09-23
ubuntu won't boot.
I can select the installation from the grub menu, so it is still there.
I just get a slightly off-black screen after the Ubuntu logo.
No idea what can have happened unless there was a kernel rebuild in the latest update and it has crashed my graphics driver.
Thanks.
:-)

---

### Post by oldfred on 2014-09-23
What video driver have you installed. 
If you install directly from vendor like nVidia you have to update with every kernel update. Generally better from repository.
Can you boot with nomodeset or from the recovery mode which is second line in grub menu?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by CJ_Hudson on 2014-09-24
Hi thanks that's helpful advice.
I was using the Catalyst Control Centre Beta AMD drivers and Steam with Playonlinux to run I game I was playing.
I tried various options in the boot menu. I also tried inserting a Ubuntu disc but no luck- couldn't see any "repair" option.
Sorry but I have no idea what nomodeset means or what it does?
I have been out of the Ubuntu loop for a few years and have forgotten most things! Just explain in words of one syllable and we can get somewhere. :-)

---

### Post by oldfred on 2014-09-24
Can you get to grub menu.
If not maybe hold shift key from BIOS or if UEFI press escape key. 

Then see above for details on replacing quiet splash with nomodeset.
Or in grub menu try booting from second line or recovery mode. May be sub menu now.

---

### Post by CJ_Hudson on 2015-01-18
Thanks for the help. Sorry didn't have time to repair, reinstalled.

---

