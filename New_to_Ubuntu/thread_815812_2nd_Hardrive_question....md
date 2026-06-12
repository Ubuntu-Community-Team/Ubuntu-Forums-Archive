---
title: "2nd Hardrive question..."
date: 2008-06-02
forum: New to Ubuntu
---

### Post by bertlacy on 2008-06-02
I have 2 hard drives installed, one for OS and second for backup.  The only problem is on my backup hard drive I accidentally installed Ubuntu on that drive and now I need to remove it.  

What are you guys thoughts on what steps I should take to accomplish this...

---

### Post by iaculallad on 2008-06-02
> **bertlacy said:**
> I have 2 hard drives installed, one for OS and second for backup.  The only problem is on my backup hard drive I accidentally installed Ubuntu on that drive and now I need to remove it.  

What are you guys thoughts on what steps I should take to accomplish this...

Boot from your Ubuntu LiveCD, use the GParted partition manager to delete the partitions created by your second installation on the second hard drive and format it to any filesystem you want. Then (Assuming that you are now dual booting), remove the entry of your second Ubuntu installation on your GRUB menu.

---

### Post by jualin on 2008-06-02
If you dont have anything important in that drive you should format it completely to remove Ubuntu. I would boot a live cd and just use the partition editor to format the Backup HDD

---

### Post by bertlacy on 2008-06-02
Thanks guys

---

### Post by meierfra. on 2008-06-02
If you do not have a second ubuntu on the internal drive:

There is a fair chance that Grub got installed to the MBR of the  internal drive. If this is the case you will have the fix your MBR. Click on FixMBR in my signature for details.


If you do have a second ubuntu on the internal drive:

There is a fair chance that you have to reinstall Grub. Click on FixGrub in my signature for details.

---

