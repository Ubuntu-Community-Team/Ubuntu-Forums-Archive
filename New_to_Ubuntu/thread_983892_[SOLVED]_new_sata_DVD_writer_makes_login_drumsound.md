---
title: "[SOLVED] new sata DVD writer makes login drumsound LOOP"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by Arthur Millar on 2008-11-16
I installed a new sata drive and now i get the login sound looping over an over 
these things seem really unrelated so how is it possible

---

### Post by barbedsaber on 2008-11-16
MAN that must be a pain.
If you want to disable login sounds
system>preferences>login Window>Accessibility Untick login screen ready
I don't know how to actually fix your problem, but this may preserve your sanity.

---

### Post by Arthur Millar on 2008-11-16
WTF 
My hardy worked better with a broken IDE DVD writer 
than a brand new sata DVD writer
WTF WTF WTF

---

### Post by Arthur Millar on 2008-11-16
> **barbedsaber said:**
> MAN that must be a pain.


i am going to become a serial ubuntu killer heheh

---

### Post by Arthur Millar on 2008-11-16
Linux hates me 
i feel like im trying to write with the opposite hand

---

### Post by Arthur Millar on 2008-11-16
just did a complete fresh install 
and the sound loop problem IS STILL THERE 
i cant work without an optical drive either!! (linux won't boot)
old writer is dead now

---

### Post by doug1212 on 2008-11-16
Just check that you have the latest bios firmware on the mother board, I have foxconn board that gave me no end of trouble with SATA and I had to nag them to release a bios that worked they seem to release firmware after people find problems :(
Doug.

---

### Post by Arthur Millar on 2008-11-16
> **doug1212 said:**
> Just check that you have the latest bios firmware on the mother board, I have foxconn board that gave me no end of trouble with SATA and I had to nag them to release a bios that worked they seem to release firmware after people find problems :(
Doug.

thanks 
i narrowed it down to a bios setting "legacy IDE"
my old optical drive was IDE so i had to change From "native IDE" to "Legacy IDE" i just reverted cause my new one is SATA

---

