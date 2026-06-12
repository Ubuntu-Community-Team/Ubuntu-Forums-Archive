---
title: "Detecting/mounting existing RAID5 from dead NAS"
date: 2012-06-22
forum: New to Ubuntu
---

### Post by jameslaidler on 2012-06-22
Hello there,

I've been unfortunate enough to have a Patriot Javelin S4 NAS for the past year which, after several hiccups (web admin interface dying, DNLA function stopping), I decided to return and get a refund.  I had four 2TB drives in a RAID5 array which was working perfectly fine until I sent the NAS back, so I've no reason to believe the array is corrupted in any way.  I'm an idiot though as this is the only copy I've got of the data (thinking RAID5 would protect it...)

I've just build myself a new PC and installed Ubuntu successfully (Desktop, as I prefer to have a GUI), running off a new separate 500GB drive. Once I knew that was all working fine, I popped in the four RAID drives. Ubuntu now sees them in Disk Utility (devices /dev/sdb, c, d and e respectively), says they're each 2TB RAID components, healthy and not partitioned.

How do I access the data on the array and go about using them as such? Things I've read suggested even though the Javelin was a hardware RAID, since it put the RAID info on the start of each disc that Linux should be able to read them with no problem...

Best,
James

---

### Post by mlentink on 2012-06-22
I'm no expert. But I am pretty certain that Desktop does not install LVM, which I guess would be needed to mount the raid-volume. So I'd read up on that.

I found this, which might help: [http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CFQQFjAA&url=http%3A%2F%2Fwww.alphadogtechs.com%2FRAID_recovery_procedure.pdf&ei=hoTkT66UEpDz-gbTj8iVCg&usg=AFQjCNEY1nIxQwGVePRLB_ppApbyIABbtw&sig2=KVku88aMPBFT7lODELTa5w](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CFQQFjAA&url=http%3A%2F%2Fwww.alphadogtechs.com%2FRAID_recovery_procedure.pdf&ei=hoTkT66UEpDz-gbTj8iVCg&usg=AFQjCNEY1nIxQwGVePRLB_ppApbyIABbtw&sig2=KVku88aMPBFT7lODELTa5w)
 and: [http://ubuntuforums.org/archive/index.php/t-1443945.html](http://ubuntuforums.org/archive/index.php/t-1443945.html)

---

