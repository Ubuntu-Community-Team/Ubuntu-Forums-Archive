---
title: "XP Mem issue"
date: 2009-01-25
forum: Other OS Talk
---

### Post by fistfullofroses on 2009-01-25
I built a new machine yesterday. Nothing much. mATX, low pro case, 1.6gHZ AMD AM2 sempron 64, 4gb DDR2 800, 100gb SATA HDD, DVD+RW drive, 275W psu, etc... It's a decent machine. I know that WinXP is limited to 3.25gb of RAM, and there is this PAE driver or something that allows one to use 4gb, but it was released by intel. Will it work with AMD? I need XP for various compatibilities. Hence the reason I built a machine for it. Despite the need for XP I have some resource requirements too, so getting the extra 1gb of RAM would really help. Anyone have thoughts or ideas? If I can use PAE how do I go about setting it up? I have used BSD and Linux all my life. No idea how this Windows stuff goes... sorry.

---

### Post by Frak on 2009-01-25
PAE is not Intel's technology, it's a generic technology. What PAE does is extend the processor bits to 36-bit to allow addressing up to 64GB. No application is allowed to address more than 3.2GB though.

Now, XP does not have a full implementation of the PAE technology. It allows it to the point of being able to use the NX/XD bit, nothing else. Your best bet would be to use the 64-bit edition of Windows XP, which is fully compatible with 32-bit Windows XP applications.

---

### Post by fistfullofroses on 2009-01-25
> **Frak said:**
> PAE is not Intel's technology, it's a generic technology. What PAE does is extend the processor bits to 36-bit to allow addressing up to 64GB. No application is allowed to address more than 3.2GB though.

Now, XP does not have a full implementation of the PAE technology. It allows it to the point of being able to use the NX/XD bit, nothing else. Your best bet would be to use the 64-bit edition of Windows XP, which is fully compatible with 32-bit Windows XP applications.

Well, I don't have 100-200 dollars to spend on yet another OS (especially one this old). Also, I would then have to re-install everything. I guess I will just go ahead and use it as is. Thank you though! If I ever get my hands on 64bit XP, I will go ahead and back everything up and reinstall.

---

