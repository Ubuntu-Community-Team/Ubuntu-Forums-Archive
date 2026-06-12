---
title: "Unable to install ubuntu :("
date: 2008-07-18
forum: New to Ubuntu
---

### Post by bkamalnivas on 2008-07-18
I am not able to install ubuntu...it gets hanged in the
UBUNTU SCREEN...pls help

---

### Post by Cypher on 2008-07-18
What version of Ubuntu and what Ubuntu screen?

---

### Post by bumanie on 2008-07-18
Need more information such as version of ubuntu, system specifications etc. You may need to try the alternate cd (text-based installer) as long as your system specs are OK.

---

### Post by sp0nge on 2008-07-18
I would also put the disk in another machine if possible. Try to check the integrity of the disk just in cases.

---

### Post by WRDN on 2008-07-18
When the GRUB bootloader appears, press "e" to edit the boot options. Select the 2nd option and press "e" again, then remove the words "quiet splash" from the end of the line. Now, press "b" to boot Ubuntu, and it will display text rather than splash screen, allowing you to see the errors thay may occur.

---

### Post by LittleLORDevil on 2008-07-18
Could be also that Ubuntu can't find a proper default graphics driver. Best route is alternate CD.  I have had this issue before.

---

### Post by bkamalnivas on 2008-07-18
8.04 desktop edition...
on checking for integrity - it diplays 45 error file - i ve tried 3 CDS(same result)

---

### Post by Mhurst1 on 2008-07-18
Have you tried at the slowest speed?

---

### Post by avtolle on 2008-07-18
Please take a look at this: [http://psychocats.net/ubuntu/iso](http://psychocats.net/ubuntu/iso) There are at least two reasons for the bad CD; one, a corrupted iso from the download (thinking this might be the case given the same results for 3 CDs), which is checked by the md5sum process; two, burning too fast. For me, given my mature hardware, I burn to CD-R at 4x. Anyway, give it a read and see if it helps you.

---

### Post by SunnyRabbiera on 2008-07-18
usually the slower speed the better, also make sure you are burning your iso correctly.

---

