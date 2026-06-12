---
title: "can't shut down"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-11-22
I fixed up an old Dell xps200 with 1GB ram and have everything working fine except shutdown restart hibernate etc. Whether from a menu or terminal it won't shut down without holding down the power button. I would like shutdown, hibernate, suspend to work but could live with just shutdown. Is there a way to figure out the problem as it runs real nice except for this.I am running 11.04

---

### Post by philinux on 2011-11-22
> **cmcanulty said:**
> I fixed up an old Dell xps200 with 1GB ram and have everything working fine except shutdown restart hibernate etc. Whether from a menu or terminal it won't shut down without holding down the power button. I would like shutdown, hibernate, suspend to work but could live with just shutdown. Is there a way to figure out the problem as it runs real nice except for this.I am running 11.04

It could be network manager. Right click it and untick enable networking. Try then to shutdown or restart in the normal way.

If this works then there is a permanent fix. When I remember where I put it.

---

### Post by cmcanulty on 2011-11-22
No that didn't work what is weird is the monitor goes to sleep and even if I puish the monitor button nothing comes up but the hard drive and fan  never stops

---

### Post by philinux on 2011-11-22
> **cmcanulty said:**
> No that didn't work what is weird is the monitor goes to sleep and even if I puish the monitor button nothing comes up but the hard drive and fan  never stops

Ok. Not that then.

I had an old Pentium pc and I had to add acpi=force IIRC. I think that went in the grub boot lone. I eventually flashed the BIOS and that fixed it.  The BIOS was pre 1999.

This may not be your problem though.

---

### Post by cmcanulty on 2011-11-22
I think this is a early to mid 2000s machine from whar I could tell. How would I update the bios without screwing up the ubuntu boot?

---

### Post by cmcanulty on 2011-11-29
Solved I installed the mint 12 repositories and files and now it shuts down and suspends properly.So I don't know what exactly fixed it.

---

