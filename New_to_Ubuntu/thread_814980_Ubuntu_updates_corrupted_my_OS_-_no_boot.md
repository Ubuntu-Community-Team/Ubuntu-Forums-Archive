---
title: "Ubuntu updates corrupted my OS - no boot"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by cwmoser on 2008-06-01
I got a number of updates Friday for my Gutsy Ubuntu and after rebooting, my OS will no longer boot.  I wondering if this was via the Update or was it something else I might have done.  In any case, even after attempting to edit the grub menu, all I can get now is Ubuntu banner and the progress bar will not move.

Anyone else experiencing this?  Any ideas on a fix?

Thanks

Carl

---

### Post by CameO73 on 2008-06-01
Have you tried one of the previous kernels in the boot menu?

---

### Post by cwmoser on 2008-06-01
I only had one instance of Ubuntu on my hard drive.  The recovery would not boot either.

I'm bringing up Ubuntu Hardy Studio and getting that setup.  Still, I would like to boot my Gutsy OS as I had it configured the way I liked it.

Carl

---

### Post by durand on 2008-06-01
Try changing the grub boot line to show extra messages. From the line, remove quiet and add verbose. If you want more information, you can remove splash as well.

That should help with debugging.

---

### Post by cwmoser on 2008-06-01
Read somewhere that there was an errant Update push last Friday 30May2008.

Anyway,after removing the "Quiet" from the Grub selection, the error is:

"Failure registering capabilities with primary security module"


Carl

---

### Post by philinux on 2008-06-01
Can you edit your menu.lst from the livecd.


This is how mine is set to show three kernels. I'm guessing yours is set to show 1.
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=3


See if you can set the howmany= to more than one.

That should let you then boot with an older kernel

---

### Post by durand on 2008-06-01
That error sounds horrible :(

---

