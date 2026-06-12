---
title: "LinuxMint with Vista?"
date: 2007-06-02
forum: Other OS Talk
---

### Post by Milt888 on 2007-06-02
I have a 120g (hda) with Vista and another 320g (hdb) with a few BU files on it.
I wanted to dualboot Linuxmint without affecting Vista.
Should I shrink hda with Vista, partition and install there or install Mint on hdb ?
I know that Feisty's grub works ok with a Vista dualboot now, and was wondering whether anyone has tried it with Mint's bootloader.
I'd thought about just installing grub to the Mint partition and using EasyBCD.
Anyone dualbooted Mint with Vista and if so how did you do it ?
Thanks for any help.

---

### Post by Computer Guru on 2007-06-03
You can do it by exactly what you just said.
Install Mint's bootloader to the partition, and EasyBCD will do the rest.

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Milt888 on 2007-06-03
> **Computer Guru said:**
> You can do it by exactly what you just said.
Install Mint's bootloader to the partition, and EasyBCD will do the rest.

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

Thanks for the link; hadn't seen that.
I've seen where some people have used Fiesty's grub directly on Vista's MBR and it worked, but didn't know whether grub worked the same way in Mint.
People have had all kinds of problems with older Ubuntu versions and Vista.

---

### Post by Computer Guru on 2007-06-04
I've tested EasyBCD with Ubuntu 6 and 7, no problems whatsoever :)
 
Good luck to you!

---

