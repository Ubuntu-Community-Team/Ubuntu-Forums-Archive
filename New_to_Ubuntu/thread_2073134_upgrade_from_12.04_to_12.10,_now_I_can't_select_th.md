---
title: "upgrade from 12.04 to 12.10, now I can't select the windows option on the grub menu"
date: 2012-10-19
forum: New to Ubuntu
---

### Post by squakie on 2012-10-19
I performed an update to go from 12.04 to 12.10.  This is on a dual-boot desktop with Windows 7.  After the update, I can no longer access the Windows option on the grub menu.  It's as if my USB keyboard isn't being recognized at that point whereas it used to work before the update.

I also have another thread open on problems encountered when going to 12.10.

I'm starting to think that perhaps I should go back to 12.04 via a completely clean install.  I just sort of hate the idea of doing so.

Anyone have any ideas on why I can't select the Windows option on the grub menu?

---

### Post by squakie on 2012-10-19
Apparently rather than just reboot, I needed to physically power off and back on - this seems to have allowed the keyboard to be "seen" again at the grub menu.

---

### Post by rburkartjo on 2012-10-19
have you tired to run sudo update-grub while in your ubuntu partition. i have a dual boot with win7 also and upgraded to 12.10 without any problem win7 still shows up in grub.

---

