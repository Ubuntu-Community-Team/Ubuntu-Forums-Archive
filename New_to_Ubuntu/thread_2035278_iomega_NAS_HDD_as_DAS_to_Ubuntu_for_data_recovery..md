---
title: "iomega NAS HDD as DAS to Ubuntu for data recovery."
date: 2012-07-30
forum: New to Ubuntu
---

### Post by parry1234 on 2012-07-30
Hi,
 
I am new to Linux infact i got it just so I could recover data from a HDD of an iomega NAS (Mirror raid). The drive is not showing up when I directly connect it via USB to Windows 7. This is because the NAS Box uses Linux OS the box wont work at all so I have to recover the data before I format the HDD and flash the box.
 
Can someone help me mount the HDD via USB on Linux & help me recover the data. It does not detect automatically when I plug it although the drive does shoe up in Disk Utility.
 
 
Please help !!
 
Thanks

---

### Post by steeldriver on 2012-07-30
What version of Ubuntu are you running?

If the NAS was using Linux software RAID you will likely need to install the package 'mdadm' before you can do anything. You may then be able to reassemble the array and mount it - these things can be difficult though especially if the array was left in a degraded state.

---

### Post by parry1234 on 2012-07-30
> **steeldriver said:**
> What version of Ubuntu are you running?
 
If the NAS was using Linux software RAID you will likely need to install the package 'mdadm' before you can do anything. You may then be able to reassemble the array and mount it - these things can be difficult though especially if the array was left in a degraded state.
 
 
Hi,
 
using the recent Ubuntu 12.04 LTS as Dual boot with Windows 7.
 
Thanks

---

