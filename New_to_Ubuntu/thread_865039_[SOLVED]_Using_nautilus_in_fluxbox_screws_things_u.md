---
title: "[SOLVED] Using nautilus in fluxbox screws things up"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-07-20
I just started using fluxbox and when I open Nautilus, part of the gnome desktop opens and I loose the ability to right-click the desktop, so I can't open up a shell to kill it (short cuts don't work).

I use thunar, but my brother/roommate *(who is pretty mad at me for putting "this crap" on here)* sometimes opens it by accident.

I could remove it from the menu, but I like nautilus (the way it handles ssh).

Any fixes?

---

### Post by RedSquirrel on 2008-07-20
When running nautilus with Fluxbox, you have to run nautilus with the --no-desktop option to prevent it from taking over your desktop:

```
nautilus --no-desktop
```

---

### Post by billgoldberg on 2008-07-20
Thanks.

I also like the link in your sig.

I would thank you there too, but it won't let me.

---

