---
title: "[SOLVED] Grub + xp from restored disk image"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by jimmy the saint on 2008-06-30
My intention is to wipe both HDs clean and install XP on one, Ubuntu on the other and use various partitions for home, storage and swap/page etc.  Rather than install XP again, I intend to simply populate the XP partition with a disk image I made after a fresh install with all the software installed and registered (saves hours and hours of work).
    My concern is that, since XP will not be installing, more like appearing, there will be no grub entry.  Am I worrying for no reason or will I have to manually add it, and if so how do I do it?

Thanks

JTS

---

### Post by rbanavara on 2008-06-30
First install / Clone your XP. Then install Ubuntu, it will install GRUB & add an entry to boot XP as well.

---

### Post by lswest on 2008-06-30
well, if you restore XP before installing Ubuntu it should still be recognized in the GRUB entry, since it doesn't look for if it was installed, it looks for the partition and adds an entry to that.  However, if ubuntu is already installed, and you restore XP and it's bootloader to the second disk (so that GRUB stays intact) then you will need to add an entry to GRUB.  It will look something like this:

```
title Windows XP
root (hd1,0)
savedefault
makeactive
chainloader +1
``` since it's a dual disk setup you may need to do this:
```
title Windows XP
root (hd1,0)
map (hd0) (hd1)
mapt (hd1) (hd0)
savedefault
makeactive
chainloader +1
``` However, try the above first.

---

### Post by jimmy the saint on 2008-06-30
So I would definitely need to do an actual installation of xp first in order to create the boot info?

---

### Post by jimmy the saint on 2008-06-30
Alright then, I will go ahead and try it.  Hopefully it is automatically detected as you say, Iswest.  Always hoping things just work, but usually work is involved!  Thanks for the responses, I will give it a try and report back.

---

### Post by lswest on 2008-06-30
Well first off, the name is actually "Lswest" :P but anyways, I don't think you'd need to actually install XP, just copy it over and restore the mbr, that should work too.

---

### Post by jimmy the saint on 2008-07-02
Sorry about that, I didn't look at the pic and those l's and I's look look the same in whatever font they're in!!  Anyway it worked like a charm.  I just restored the acronis image to the partition and grub picked it up with no trouble at all.  Thanks for the quick response on that one!!

---

