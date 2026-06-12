---
title: "[SOLVED] Grub rewriting MBR in Dual Boot"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Electrovellum on 2008-11-12
I have an MBR, rewritten by Acronis System Recovery under Vista, to add in the option to press F11 to do a Vista recovery on re-booting Vista after a fail. 

This has removed the entries by Grub to enable Ubuntu to load. No real problem, I can reinstall Ubuntu (nothing of significance in it yet!) from the DVD after deleting its Linux partitions under Vista. 

Question is: Will Grub retain the Acronis F11 option when it rewrites the MBR on reinstalling Ubuntu? If so, what do you advise?

---

### Post by Titan8990 on 2008-11-12
No, it will overwrite what Acronis has put on. Acronis has a bootable CD that you can make instead of having it write the MBR. I suggest using that and keeping it handy.

---

### Post by Electrovellum on 2008-11-12
> **Titan8990 said:**
> No, it will overwrite what Acronis has put on. Acronis has a bootable CD that you can make instead of having it write the MBR. I suggest using that and keeping it handy.
OK! That I shall do, once I find out how to create the CD. Thanks for the advice.

Just remembered, installation CD doubles as a boot CD - clever Acronis!

---

