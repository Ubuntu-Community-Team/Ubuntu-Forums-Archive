---
title: "BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by dedo678 on 2008-05-30
I installed Ubuntu about a week ago. It worked fine the whole time, perfectly actually. Until yesterday, whenever I boot it up it shows the orange loading bar. It loads for about 5 seconds then goes to:

BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Type "help" for more commands

With nothing else. Not even an error. Although, if i leave it for about a minute, errors about a drive pop up. I don't remember what they exactly say so I'm a bit stumped. I really want to continue using Ubuntu but I cannot for now. Please help. 

Also, I'm a newbie at the whole "Linux" language you use in the who command thing so please, user friendly answers.

---

### Post by quelx on 2008-05-31
at the **Loading Grub** screen hit **escape** to choose a boot option, you are currently booting into recovery mode, so choose (with the arrow keys) the first option (should not have *recovery mode* after it)

---

### Post by superprash2003 on 2008-05-31
try rebooting two or three times..

---

### Post by dedo678 on 2008-05-31
I just recently reinstalled it and so it does not have those things. 

Also, I tried starting it up in special safety modes and every time I did, it said something about an incompatible chip and that I should try an 8139too Driver.

Anyone know what that means?

---

### Post by upwinger on 2008-06-20
I am having the same problem installing Ubuntu onto a brand new Dell i530S with Vista....but I have not been able to load the live CD at all...it goes straight to DRDY ata 2.00 exception Emask 0x0Sact0x0Serr0x0action0x0frozen sychronous SCSt scan failed without progress.

This disc loaded Ubuntu fine on 2 laptops so I know the disc is ok. Is it Vista thats blocking its upload???:confused:

---

### Post by jimmynewtron on 2008-06-22
I'm having the same issue. Getting stuck on an install with the try "8139too" driver. 

Does anyone know a cause/solution to this issue?

Thanks

---

### Post by Aearenda on 2008-06-22
I suspect the 8138too thing is a red herring. Try booting with the all_generic_ide kernel parameter - see [http://ubuntuforums.org/showpost.php?p=4799028&postcount=15](http://ubuntuforums.org/showpost.php?p=4799028&postcount=15). For liveCd booting, after choosing the language press F6 and add 'all_generic_ide' to the end of the line presented, after the '--' marker.

---

