---
title: "[SOLVED] Forced Chkdsk on bootup"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by alexham on 2008-10-02
I am using ubuntu most of the time, but on rare occasions when I have to log into Windows, the system starts with Check Disc procedure, finds nothing wrong and then continues with the boot up.

Until a month ago I was using Mepis and this started happening since I changed to Ubuntu, so I am assuming that it is Ubuntu that is causing windows to Chkdsk each time.

I am running Win Pro SP3 on AMD Athlon 64X2 Dual Core Processor 4000+ with NVidia GeForce 6100 nForce 430 graphic card and NVidia HDA sound card. The motherboard is Asus M2N-MX. It has 2 hard drives and both are nearly new - 18 months.

Are these "enforced" Chkdsk checks an early indication that something is going wrong?

Thanks,

Alex

---

### Post by Paqman on 2008-10-02
> **alexham said:**
> 
Are these "enforced" Chkdsk checks an early indication that something is going wrong?


Probably not, since the check doesn't detect any errors. It's more likely that Ubuntu isn't unmounting the Windows NTFS cleanly when it shuts down.

If you boot up Windows then restart it, does it do the chkdsk on the second boot? Or is it only you last booted into Ubuntu?

---

### Post by alexham on 2008-10-03
> **Paqman said:**
> Probably not, since the check doesn't detect any errors. It's more likely that Ubuntu isn't unmounting the Windows NTFS cleanly when it shuts down.

If you boot up Windows then restart it, does it do the chkdsk on the second boot? Or is it only you last booted into Ubuntu?

It carried on with disc checking after the restart and it kept checking the same 2 partitions, not all.  One of these is empty and the other used for storage of photographs - i.e. no reason for ubuntu to access either.

I have copied the photographs onto a CD and re-formatted the partitions and the disc checking has stopped.

Problem solved, but I don't know how or why?

Thanks,

Alex

---

