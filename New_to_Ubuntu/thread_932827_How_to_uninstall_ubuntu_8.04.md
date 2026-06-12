---
title: "How to uninstall ubuntu 8.04"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by cidrisonly on 2008-09-28
I am a lover of Ubuntu. However, just for my knowledge, if something went wrong and I wanted to uninstall Ubuntu 8.04 from the computer, what would be the procedure. I installed it with live CD I got from Ubuntu's shipment. I tried a lot of stuffs, but it doesn't go completely from computer. It even gives the Error 22 and doesn't boot Windows. Another problem from not uninstalling Ubuntu, one cannot run the System recovery that brings back factory setting. Kindly someone guide me on this one.

---

### Post by zephyrcat on 2008-09-28
It sounds like you have Windows installed in dual-boot. If this is the case, first just delete the Ubuntu partitition and increase your Windows partition to fill the space (make sure to use a partitioner that wil not destroy the data in your Windows partition). Then, use your Windows CD to do some sort or restore function (I cannot remember what it is called). Basically, the point of this is to restore the Windows bootloader.

That should be it.

---

### Post by melojo on 2008-09-28
to fix the master boot record for xp insert the xp cd reboot got recovery console type
fixmbr
and sometimes you need to
fixboot

anytime I have fixed my xp installation I can get by with fixmbr

---

### Post by dgray_from_dc on 2008-09-28
> **melojo said:**
> to fix the master boot record for xp insert the xp cd reboot got recovery console type
fixmbr
and sometimes you need to
fixboot

anytime I have fixed my xp installation I can get by with fixmbr

I agree.  The reason for your error is that GrUB is still installed.  This will definitely fix your booting problem as it will overwrite GrUB.

---

### Post by cidrisonly on 2008-10-10
Hey guys thanks for your wonderful ideas. Appreciate it. However if I am not wrong, are you saying that i put the xp/ vista live CD or something of that sort and overwrite the existing ubuntu to get rid of Grub. If thats so then will my existing xp/vista remain or it will overwrite too to the new one.

Hey guys another query if you can answer me. I am having this Compaq Presario C700 Notebook PC.

Installed ubuntu 8.04 and wireless didn't work. I tried the madwifi technique from the ubuntu forums and worked. Wireless works now. but the problem is that as soon as i get into ubuntu the laptops mouse function doesn't work. is it because the hardware Atheros is still failing. Please help,

---

