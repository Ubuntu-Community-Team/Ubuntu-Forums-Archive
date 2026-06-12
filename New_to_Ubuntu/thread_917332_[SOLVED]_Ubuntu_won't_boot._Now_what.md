---
title: "[SOLVED] Ubuntu won't boot. Now what?"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by doctorbighands on 2008-09-11
I've installed a dual-boot machine with Hardy and XP. Hardy was already there, and I just finished installing XP (backward, I know, but what could I do?). I went to reinstall GRUB, and now I'm having an issue I've never seen before.

During boot, I get a series of error messages. The first one:
```
Failed to read splash image ((hd0,2)/boot/grub/splash.xpm.gz)
Press any key to continue...
```

So, I press any key, and I get what looks like an attempt to boot (it says the typical "Press ESC to enter the menu..."). After that, though, another message:
```
Error 17: Cannot mount selected partition
Press any key to continue...
```

It then takes me to the GRUB menu. If I try to boot from any of the three kernels listed, it goes back to the "Cannot mount..." message, and kicks me back into GRUB.

What have I done, and how do I fix it?

(Incidentally, I used the SuperGRUB Disc, so I know that isn't the issue.)

Thank you!

---

### Post by doctorbighands on 2008-09-11
Per further research, I am currently running a filesystem check. I will report on whether that works for me.

In the meantime, any other ideas are welcome!

---

### Post by doctorbighands on 2008-09-11
Fixed!

PROBLEM: GRUB wanted to access (hd0,2) to boot Ubuntu, but Ubuntu lives at (hd0,0).

SOLUTION: Edit /boot/grub/menu.lst

Worked like a charm!:guitar:

---

