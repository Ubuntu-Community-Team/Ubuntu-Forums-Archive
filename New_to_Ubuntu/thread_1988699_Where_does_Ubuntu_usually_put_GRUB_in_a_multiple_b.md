---
title: "Where does Ubuntu usually put GRUB in a multiple boot situation?"
date: 2012-05-28
forum: New to Ubuntu
---

### Post by murphyac on 2012-05-28
When I first installed Ubuntu on my desktop, I didn't pay much attention to where the boot loader was put.  It's a triple boot - Ubuntu, Windows XP and Xandros Linux.  Since I had trouble after my upgrade to 12.04, I am trying to re-install 12.04 from the CD.  On the partition screen, it asks me where I want to put the boot loader.

Oh dear, I want it in the same place it is now, but I have no idea where that place is.  Can someone tell me how to find out where my current boot loader is?

Thanks for any help.
Angela C. Murphy

---

### Post by wilee-nilee on 2012-05-28
> **murphyac said:**
> When I first installed Ubuntu on my desktop, I didn't pay much attention to where the boot loader was put.  It's a triple boot - Ubuntu, Windows XP and Xandros Linux.  Since I had trouble after my upgrade to 12.04, I am trying to re-install 12.04 from the CD.  On the partition screen, it asks me where I want to put the boot loader.

Oh dear, I want it in the same place it is now, but I have no idea where that place is.  Can someone tell me how to find out where my current boot loader is?

Thanks for any help.
Angela C. Murphy


Standard pc in the mbr of the hard drive that ubuntu is going to, the mbr is just three letters like sda, or sdb...etc no partition numbers.

You can make sure of this with the something other option from the live cd where to install gui, first page after has a dropdown for choices.

If you do this with 12.04 it will have the boot control.

---

### Post by murphyac on 2012-05-28
Thank you.  My Ubuntu is on sdb, so if I finally decide to do a re-install from the CD, I will now know where to tell it to put GRUB.
Angela C. Murphy

---

