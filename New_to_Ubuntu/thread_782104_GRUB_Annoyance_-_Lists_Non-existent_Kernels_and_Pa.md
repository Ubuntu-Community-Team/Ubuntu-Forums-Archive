---
title: "GRUB Annoyance - Lists Non-existent Kernels and Partitions :(.."
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Glaxed on 2008-05-04
Hi -
My computer is loving the new release, and everything is perfect except for this one Grub issue.

I had been using Gutsy, but then I decided I wanted to try the early Hardy betas, so I Gparted (that's a verb now) my disk into 2 main partitions that shared a 2.86 GB swap (that was Fesity's default swap size, so I keep it like that =p).

A week before the RC, I decided that Hardy had improved and stabilized enough to format (or should I say Gformat :D) the Gutsy partition - which I did.

But now, my Grub lists my old Gutsy kernels, and I can't edit the menu.lst on the Gutsy partition... because it's gone. How can I remove the references to non-existent kernels and partitions from the Grub menu?

Help is appreciated, thanks for reading.

---

### Post by Happy_Man on 2008-05-04
Frankly, I'm amazed GRUB is still starting, if it was running off the menu.lst in the Gutsy partition. Therefore, I can only conclude that you are using Hardy's version. So, press alt-f2, and enter ```
gksudo gedit /boot/grub/menu.lst
``` and remove all the old kernels in the manner specified in the file. Have fun!

---

