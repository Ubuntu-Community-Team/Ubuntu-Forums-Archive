---
title: "Can't find file intel.c?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Revhead on 2008-07-14
Trying to patch my kernel in Ubuntu server edition 2.6.24-16 but can't seem to find the following file?
arch/i386/kernel/cpu/intel.c
Any help appreciated?
Rev

---

### Post by Bachstelze on 2008-07-14
You know that in order to patch your kernel, you'll  have to compile it yourself, right? If you don't, think twice before doing it, as it is a very tedious process for a newbie, and it will likely require a lot of work to get it right.

---

### Post by Revhead on 2008-07-16
Thanks for your reply HymnToLife.
No, I didn't know that but I couldn't get anyone to reply to my post explaining how to do the following which prompted the question.
[http://ubuntuforums.org/showthread.php?t=858108](http://ubuntuforums.org/showthread.php?t=858108)
Any help really appreciated :-)

---

### Post by philinux on 2008-07-16
What sort of performance increase would you get for all the trouble?

---

### Post by Revhead on 2008-07-16
> **philinux said:**
> What sort of performance increase would you get for all the trouble?

A lot. 
Currently running without any L2 cache. You try disabling your L2 cache in BIOS and see what difference it makes to your rig.
In the case of the Socket 370 Celeron (PPGA) it had 128kb of L2 cache which ran at full speed compared to the PII that had 512kb but ran at half speed. 
Surely what I am asking is not that hard?

---

### Post by nowshining on 2008-07-16
actually compiling a custom kernel is NOT a tedious process - it's quite simple... especially with the tools to do it on a debian system. However it may take a bit more time if you plan on removing items, etc.. from the kernel, etc... However if you know what u want to do and leave most as default - I would say it would take roughly about 10m _ (def. minus) to configure & depending on ur cpu - about 1hr. to finish compiling - & 5m to install the debs depending on how fast ur cpu is.

Once done - reboot and re-install all the Graphic Drivers if need be - startx or /etc/init.d/gdm or kdm start

so all in all - on my P4 - it takes about 1hr and 15m to do all of the above. Of course the newer kernels will pick up ur ol' config :) of the currently running kernel.

---

