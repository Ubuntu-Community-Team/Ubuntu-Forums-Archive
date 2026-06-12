---
title: "GRUB error: Fix Minimal BASH like line editing is supported..."
date: 2016-10-15
forum: New to Ubuntu
---

### Post by hunterxhanzo on 2016-10-15
Hello. Today I updated my BIOS (with a Sony update) and since then I get the screen that says 
"minimal bash-like line editing is supported"

I tried with the steps in this tutorial but it didn't fix it:
[https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)
So I got the logs from boot-repair in this link:
[http://paste2.org/eCsa05LO](http://paste2.org/eCsa05LO)

I don't know how to proceed to be able to boot back in Windows. Any help will be really appreciated.

Thanks!

---

### Post by oldfred on 2016-10-15
You show no Linux install.

And you have grub installed to MBR for BIOS boot, but system is UEFI.
It looks like you tried to install a Linux version in BIOS mode on an UEFI system.

Change UEFI to boot in UEFI mode not BIOS mode. 

And do not ever boot anything in the 35 year old BIOS mode. The CSM/BIOS mode is just for compatibility for older systems where a user may have an old drive or has to have BIOS/MBR for some archaic reason.

---

### Post by hunterxhanzo on 2016-10-15
Hello,
What do you mean with:
"Change UEFI to boot in UEFI mode not BIOS mode."
And how to do it?

BTW, I have Ubuntu 13.10 installed with Wubi but I haven't access it in ages.

Thanks for your reply. :)
------ 
EDIT:
It seems that after enabling Secure Boot it works (I tried this before the boot-repair but not after).
Thanks for your help anyway.

---

