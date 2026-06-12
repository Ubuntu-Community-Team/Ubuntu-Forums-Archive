---
title: "MAJOR headache when trying too burn dvd's"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by keens on 2008-11-13
hey all,

i have a few DVD's i need too back-up, but all are over DVD5 size. now i have tried alot of programs, eg, xdvdshrink, DVD95, k9copy and installed wine and dvdshrink under wine cannot find any of my dvd drives. dvd::rip just stops working and doesnt do anything as soon as i start the rip. k9copy crashes and "casued the signal 6 (SIGABRT)" and does the same thing when i try to open an .iso as well.

i have tried every program i swear and an getting nowhere. can anyone help?

cheers.

---

### Post by shifty_powers on 2008-11-13
have you run

```
winecfg
```

and made sure that wine has properly set up your optical drives?

it has a habit of not doing so :D

---

### Post by PierreDeKat on 2008-11-13
I tried a lot of stuff, too, and I ended up using Brasero to create an ISO and Nautilus's burning plugin to burn *dual-layer* DVDs. That's what I did in Hardy, anyway. 

Brasero was supposed to be able to do the whole thing, except that there was a bug in whatever version came with Hardy that prevented it from burning DVD's. Hopefully they've fixed that in version 0.8.2 that comes with Intrepid.

But I haven't tried it yet to find out.

Anywho, the downside to going this route is that you have to spend a dollar for a dual-layer DVD, versus 50 cents for a single-layer DVD. It makes a little difference, but it's not a real deal-breaker or anything.

And on the upside, it takes about half the time, since there's no compression process. And you get original quality -- with all the subtitles, menus, etc. -- rather than compressed quality and minus all the special features.

---

