---
title: "Dual Boot works but Can't Boot from CDrom!"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by smausert on 2008-09-24
Newbie here to linux.  Got my system all set up dual booting with Ubuntu/Win2K (Master/slave) which works great.  Now I find I can't boot anything from the CDRom.  Yes, my cdrom is listed ahead of the hds in my bios settings.  Floppy can be used to boot.  CDRom is useable in ubuntu and can write/read to it.  During post up, message says there is a bootable cd in the drive!  Anybody got a clue?  Should boot..... and it definitely was booting earlier cause I used it to install ubuntu on the drive!!!!  Dual boot problem????

---

### Post by Tatty on 2008-09-24
Ubuntu will not have altered your computer's ability to boot from CD.

Check the CD you are trying to boot from, it may be a bad burn.  What are you trying to boot?

---

### Post by yragrelluf on 2008-09-24
try a different bootable cd, and check the settings in the system bios.

---

### Post by smausert on 2008-09-24
Bios settings are correct as I stated.  Tried different bootable cds that worked before including the ubuntu install disk.  Would like to boot up diskcopy as I would like to make an image of this disk for protection - hearing a little disk noise...

---

### Post by smausert on 2008-09-24
Thanks for the input. Just wanted to see if this could be related to linux......  Back to more sleuthing.....

---

### Post by smausert on 2008-09-24
Solution: The CDRom was on a Promise Ultra 100 card.  I moved the CDRom to where sdb was and moved sdb to the first master on the Promise Ultra 100 card maintaining the correct mapping for grub.  I have booted from the promise before so not sure why this works but it does. All is well and it all works ..... dual boot Ubuntu/W2k; CDRom boot capability and Easeus Disk Copy bootable cd!  Just an FYI in case....

---

