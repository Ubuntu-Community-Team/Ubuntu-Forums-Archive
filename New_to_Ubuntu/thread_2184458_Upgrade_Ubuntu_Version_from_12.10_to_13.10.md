---
title: "Upgrade Ubuntu Version from 12.10 to 13.10"
date: 2013-10-29
forum: New to Ubuntu
---

### Post by azizulalamtoton on 2013-10-29
Dear all,

This is my first thread in Ubuntu forum. I am using Ubuntu 12.10 and Windows 7 with dual boot. The dual boot was done through grab or grab2 (I hardly remember as far I know). Now I want to Upgrade my Ubuntu version from 12.10 to 13.10 without having any touch on Windows 7 OS. So finally I want a dual boot option of Ubuntu 13.10 and Windows 7.
 
Thanks

---

### Post by fantab on 2013-10-29
If you do a upgrade with update-manager you have to first upgrade to 13.04 then to 13.10. If you are lucky after long hours you will be upgraded to 13.10.

To save the trouble and keep things simple do fresh and clean install of Ubuntu 13.10 replacing 12.10

Do you have a separate /home partition? If you do then doing a clean install can be easy with respect to DATA. If NOT, Do a **BACKUP of all your important data** before you attempt upgrade.

---

### Post by azizulalamtoton on 2013-10-29
I have a slow internet connection. I think a fresh installation will be better for me. I have separate  /home partition. Is 13.10 going to make a auto Dual boot or I have to do the task that I had done before with grab2?

---

### Post by fantab on 2013-10-29
Its not 'grab', its GRUB (GRand Unified Bootloader) and you don't have to do anything special. But I would like to know what you did "to do the task that I had done before with grab2?"

---

### Post by martinr on 2013-11-09
Just make sure that you don't boot the installation CD with a UEFI boot sequence if your HD structures is MSDOS with MBR.
(See: [this thread]("http://ubuntuforums.org/showthread.php?p=12030957#post12030957"))

---

### Post by Bucky Ball on 2013-11-09
> **fantab said:**
> Do a **BACKUP of all your important data** before you attempt upgrade.

Do a backup of your data whichever way you choose to go.

---

