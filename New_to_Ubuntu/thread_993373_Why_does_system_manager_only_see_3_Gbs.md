---
title: "Why does system manager only see 3 Gbs"
date: 2008-11-25
forum: New to Ubuntu
---

### Post by djowtlawz on 2008-11-25
Maybe its not such a big deal but for some reason system manager only detects 3 out of my 4 Gbs of RAM. I thought it was just ubuntu but I tried Fedora and the same results...any help?

---

### Post by taurus on 2008-11-25
32bit can only detect 3.2GB max even if you use windows.  So, if you have 4GB and your CPU supports 64bit, install 64bit if you want to use all your RAM.

---

### Post by Zzl1xndd on 2008-11-25
> **djowtlawz said:**
> Maybe its not such a big deal but for some reason system manager only detects 3 out of my 4 Gbs of RAM. I thought it was just ubuntu but I tried Fedora and the same results...any help?

32-bit OS's can only see 3.2(If I'm not mistaken) You would need to move up to 64-bit Ubuntu to see the rest.

---

### Post by jamesrl on 2008-11-25
I bet it sees 3.2 Gb, rather than 4.  It is because 32 bit architectures can only easily point to 2^32 = 4*(1024)^3 memory locations using just one word per memory location.  However, some pointers to memory locations are used by the system for non-memory locations, so you can't access all 4 Gb.

If your hardware supports 4Gb, you can try ubuntu server, which allows you to access 4 Gb through [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension").  A better (more natural) approach is to just move to a 64 bit architecture.  Note, motherboards only support so much memory as well, so it could just be that there is a hardware imposed limit at 3Gb (instead of 3.2 Gb, which is a problem of 32bit limit).

---

