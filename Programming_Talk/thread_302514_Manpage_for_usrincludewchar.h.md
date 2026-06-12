---
title: "Manpage for /usr/include/wchar.h"
date: 2006-11-18
forum: Programming Talk
---

### Post by MWAAAHAAA on 2006-11-18
Does anyone know what package to install in order to get the manpages for the functions defined in /usr/include/wchar.h (the particular function I was looking for was wcstof).

---

### Post by po0f on 2006-11-18
MWAAAHAAA,

It might be in manpages-dev.

---

### Post by MWAAAHAAA on 2006-11-18
> **po0f said:**
> MWAAAHAAA,

It might be in manpages-dev.

It isn't.

---

### Post by po0f on 2006-11-18
MWAAAHAAA,

I just looked myself and was about to post [this link](http://www.die.net/doc/linux/man/man3/wcstof.3.html).  It's weird that's it's not there.

---

### Post by llonesmiz on 2006-11-19
You need to install manpages-posix-dev:

sudo apt-get install manpages-posix-dev


Good luck.

---

### Post by MWAAAHAAA on 2006-11-19
> **llonesmiz said:**
> You need to install manpages-posix-dev

That did it. Thanks.

---

