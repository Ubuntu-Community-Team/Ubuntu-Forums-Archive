---
title: "Will Windows 8 boot up if..."
date: 2013-06-08
forum: New to Ubuntu
---

### Post by gigenieks on 2013-06-08
Hello!

I have dual-boot setup (Win 8 + Ubuntu). Both operating systems are installed on separate hard drives.
Let's say I mess up GRUB somehow and can't log in neither in Windows nor in Ubuntu.

If I remove that HDD which contains Linux & GRUB I should be able to boot in Windows, right?

---

### Post by newb85 on 2013-06-08
That depends on details you have not provided.  

Is Windows' Boot Manager on the drive containing Windows, while GRUB is on the drive containing Ubuntu?  If so, then simply telling your BIOS to boot from the drive containing windows should bring up Windows, regardless of the state of Ubuntu or GRUB (and regardless of whether the Ubuntu drive is still connected).

If, however, you *replaced* Windows Boot Manager with GRUB, then no, your Windows will not boot up without some work if you somehow mess up GRUB.  My suggestion in this case is that you boot from a LiveDVD or USB and run Boot-Repair.

---

