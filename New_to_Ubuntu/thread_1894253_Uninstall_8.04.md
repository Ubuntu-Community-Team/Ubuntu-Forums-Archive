---
title: "Uninstall 8.04"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by imjim on 2011-12-12
How do I uninstall Ubuntu v8.04. Also running Windows XP. Tried uninstall using add/remove programs.... didn't work. Any recommendations? Thanks

---

### Post by Lisiano on 2011-12-12
First of. Are you using Wubi or do you dual boot?
Also. Do you have a recovery CD of Windows XP

---

### Post by PirateKarma on 2011-12-12
Depends on how you installed Ubuntu. If you popped in the cd and installed while you were still logged onto Windows then you have a wubi install, but seeing as how you dont have it listed in your add/remove programs I'm guessing thats not what happened. I reccomend finding your Windows Xp recovery disc seeing as how when we uninstall 8.04 your bootloader while remain as grub, and this causes problems. The recovery cd still set your computer to the default Windows XP bootloder.

---

### Post by mikechant on 2011-12-12
Assuming it's not a Wubi install, once you've reset the bootloader as per the above post, you still need to recover the space allocated to Ubuntu.
This is probably best done by booting from a Ubuntu LiveCD/USB and using Gparted to delete the non windows partition/s. (probably / and swap, maybe /home as well, they will typically show up as type = ext4 or type = swap for the swap partition).

Once you've deleted these partitions (and the containing extended partition if it's now empty), reboot into Windows and use the Windows disk utility to expand the main windows partition into the free space. It is best to use the Windows disk utility for this bit since Windows is know to throw a fit sometimes if something else touches its partitions.

---

### Post by oldos2er on 2011-12-12
> **mikechant said:**
> Assuming it's not a Wubi install, once you've reset the bootloader as per the above post, you still need to recover the space allocated to Ubuntu.
This is probably best done by booting from a Ubuntu LiveCD/USB and using Gparted to delete the non windows partition/s. (probably / and swap, maybe /home as well, they will typically show up as type = ext4 or type = swap for the swap partition).

Once you've deleted these partitions (and the containing extended partition if it's now empty), reboot into Windows 

[S]This is backwards,[/S] OP needs to restore Windows' boot loader first, reboot into Windows, then delete/format the old Ubuntu partitions. If you delete Ubuntu partitions first, grub's first stage will be left in the MBR with no stage 2, hence no boot.

---

### Post by mikechant on 2011-12-20
> This is backwards,

I think you misread my post.

I said "once you've reset the bootloader.(as per previous post, with the windows recovery CD)...delete the Ubuntu partitions"
i.e. reset the bootloader *first*, then delete the ubuntu partitions exactly as you are saying.

---

### Post by oldos2er on 2011-12-20
> **mikechant said:**
> I think you misread my post.


Thanks for the correction.

---

