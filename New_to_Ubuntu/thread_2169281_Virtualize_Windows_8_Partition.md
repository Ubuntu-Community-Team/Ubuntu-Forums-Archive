---
title: "Virtualize Windows 8 Partition"
date: 2013-08-21
forum: New to Ubuntu
---

### Post by davidallen353 on 2013-08-21
I have a laptop with a HDD and SSD. The HDD has a full install of Windows 8 and the SSD has Ubuntu 13.04. I have been running as a dual-boot, but would like to run Ubuntu almost exclusively. There are, however, a few pieces of software that only run in Windows and require significant resources, so I must maintain the ability to dual-boot. 

Is it possible to virtualize my Windows partition within Ubuntu, preferably using virtualbox or another free alternative? I only have a few GB free on my SSD, so I can't create a complete virtual machine.

---

### Post by TheFu on 2013-08-21
Probably not, based on your storage and existing Microsoft license limitations.  Chances are that the license for your Windows install is tied to the specific hardware and may not work at all under any virtual machines. You can buy a different license and reinstall into a VM, but only after you have wiped the current Win8 install.

You might be able to shrink the current Win8 partition size.  If you could boot Ubuntu and post the output from 
**$ sudo parted -l**
then we'll have more information to make better suggested steps. At this point, the Microsoft license is your big issue, I fear.

I do not know **anyone** who has successfully pointed a VM tool at a hardware install and gotten it to boot. Virtual hardware and real hardware would need to be identical for that to work. On a laptop especially, that is nearly impossible.

---

### Post by Mark Phelps on 2013-08-21
Virtual machines use the host machines drivers -- and in this case, the Win8 drivers are likely to be both better and more complete (given this is a laptop) than the Linux drivers.

Also, if you do decide to shrink the Win8 OS partition, do NOT use GParted to do this.  Doing so risks corrupting the Win8 filesystem and rendering it unbootable.  Instead, use the Win8 Disk Management tool to do that.  

In Win8, you find this from the start screen search by entering Computer Management and then selecting Disk Management.

---

