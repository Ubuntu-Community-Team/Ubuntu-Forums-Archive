---
title: "Ubuntu Desktop vs Virtual Machine"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by mdonders on 2013-08-23
Hello All,

I recently received a laptop from a friend that he wasn't using anymore to do some development on and had a question as far as performance of Ubuntu Desktop vs Ubuntu in a VM. The computer has a Intel P2600 and 6GB RAM (can be upgraded to 8GB) and was wondering if performance of Ubuntu inside of a VM would be decent enough for something like doing Android Development. I doubt I would run the emulator, but rather just use my device as the debugging target.

Would a VM be able to handle this if the memory was allocated correctly?

Thank you in advance - please let me know if you require any more information.

---

### Post by lukeiamyourfather on 2013-08-23
That processor has no hardware virtualization feature (Intel VT-x in this case). That means the virtual machines will run *very slow*. I would install Ubuntu or dual boot.

[http://ark.intel.com/products/50176/Intel-Pentium-Processor-P6200-3M-Cache-2_13-GHz](http://ark.intel.com/products/50176/Intel-Pentium-Processor-P6200-3M-Cache-2_13-GHz)

---

### Post by mdonders on 2013-08-23
> **lukeiamyourfather said:**
> That processor has no hardware virtualization feature (Intel VT-x in this case). That means the virtual machines will run *very slow*. I would install Ubuntu or dual boot.

[http://ark.intel.com/products/50176/Intel-Pentium-Processor-P6200-3M-Cache-2_13-GHz](http://ark.intel.com/products/50176/Intel-Pentium-Processor-P6200-3M-Cache-2_13-GHz)

Oh alright - that solves that problem.

Dual boot it is. I notice that 64-bit doesn't have a Windows installer so just need to create a LiveDisc and then install alongside Windows, correct?

Thanks again for your help.

---

### Post by lukeiamyourfather on 2013-08-23
Yup, shrink the Windows partition using the utility in Windows before you try to install Ubuntu. Be sure to backup anything on the laptop you don't want to lose because sometimes it doesn't work (resizing the partition that is). If you have a USB flash drive you can use that to install too.

---

