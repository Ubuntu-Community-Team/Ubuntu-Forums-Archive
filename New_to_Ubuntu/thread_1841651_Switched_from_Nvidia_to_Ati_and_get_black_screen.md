---
title: "Switched from Nvidia to Ati and get black screen"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by Warpnow on 2011-09-09
I had an nvidia 8400gs installed with proprietary drivers. I switched to a radeon HD 6670 and can't get my computer to boot so I can uninstall the nvidia drivers. Safe mode does not boot...

I can see the bios, can boot into windows.

I just need to get to a command line to remove the nvidia drivers and install the ati ones.

Any ideas?

---

### Post by heyandy889 on 2011-09-09
Maybe try putting the old graphics card back in? Then you could switch to free drivers. Once you're "free," you could power off, remove the video card, and try booting up. Good luck, my man!

---

### Post by Wim Sturkenboom on 2011-09-09
Press 'e' when the grub menu shows. Find the line with *_quiet splash_* and replace *_quite splash_* by *_text_*. Press <ctrl>x to boot; this will take you to a console. Login and you can remove the proprieteray driver. I can't recall if the driver asks you to uninstall or the driver has a *_-uninstall_* option.

Alternative: use recovery mode, drop to a root shell and do the exercise from there.

---

