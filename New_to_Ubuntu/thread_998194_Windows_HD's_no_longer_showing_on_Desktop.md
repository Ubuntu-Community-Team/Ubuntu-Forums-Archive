---
title: "Windows HD's no longer showing on Desktop"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by garyed on 2008-11-30
I'm running 7.10 dual booting with XP. I have 3 HD's 2 dedicated for XP & 1 dedicated for Ubuntu. Booting to Ubuntu my 2 Windows drives were always on my Desktop & now suddenly they're gone, not even under Places. They're mounted in fstab & I can access them in terminal under /media/c_drive or(d_drive)
with no problem but they don't show up on the Desktop or Nautilus like they used to. There are just two blank spaces on my desktop where they used to be.
When I would click on Places>Computer they don't show up any more either.
One other thing is that when they used to show up on my Desktop they never had the same name as what they were mounted as in fstab so I could access them from two different places if that makes sense.
Any ideas?

---

### Post by taurus on 2008-11-30
When you use windows, make sure you shut down windows cleanly because if you don't, Ubuntu won't read/mount a corrupted ntfs filesystem without the force option.

---

### Post by garyed on 2008-11-30
I wouldn't say this is solved but after a couple more reboots everything started working normally like before. The drives now show up where the empty spaces on the desktop were & I didn't change anything.

---

