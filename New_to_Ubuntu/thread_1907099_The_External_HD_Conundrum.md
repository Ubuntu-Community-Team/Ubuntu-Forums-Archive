---
title: "The External HD Conundrum"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by marc11657 on 2012-01-10
Using Windows 7 I have partitioned my 2TB External USB HD. It now has 100GB free to install Ubuntu. 

I burnt the install CD and followed the instructions to install onto the now unformatted 100GB bit of space on the External. I had to split the unformatted space allocating space for root and space for scrub. then it allowed me to install.

Installation completed and the computer restarted. The problem is that I get the Missing NTLDR error.

Does anyone know of the most simple fool proof way to solve this?

btw the rest of my external hard drive contains data that i want to keep. i only want to use the 100gb for ubuntu use

Thanks! Marc

---

### Post by wolfen69 on 2012-01-10
> **marc11657 said:**
> 

Installation completed and the computer restarted. The problem is that I get the Missing NTLDR error.


Check your BIOS and see which drive is set to boot first.

---

### Post by marc11657 on 2012-01-10
it's the external... My internal HD has windows 7 installed on it, which boots up fine when the external isn't plugged in.

---

### Post by wolfen69 on 2012-01-10
Seems to me that you will need to reinstall grub. [https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2) But keep in mind that if you reinstall it, the external drive will need to remain plugged in during boot up. Then just make sure that the external is listed first in the bios.

---

### Post by Mark Phelps on 2012-01-11
Windows 7 does NOT use NTLDR -- that is used by Windows XP.

If it was Windows 7 not loading, it would complain about BOOTMGR.

---

