---
title: "I need to find libsndfile-1.0.2"
date: 2018-10-02
forum: New to Ubuntu
---

### Post by ghimes04 on 2018-10-02
I'm trying to install mednafen version 1.21.3 and the terminal says:
configure: error: *** libsndfile >= 1.0.2 not found!
now I know what to do  I just cant find anywhere that has the file. all i can find is more recent versions like 1.0.25. If anyone can find a place that I can get this file please tell me. thanks.
:)

---

### Post by wildmanne39 on 2018-10-02
*Thread moved to **New to Ubuntu for a more appropriate fit**.*

---

### Post by Dennis N on 2018-10-02
> configure: error: *** libsndfile >= 1.0.2 not found!

There is **libsndfile1**. Current version is 1.0.28.

> all i can find is more recent versions like 1.0.25
You don't need 1.0.2 specifically; version 1.0.28 satisfies >= 1.0.2

Also,

the package **libsndfile1** contains the files:
[B]libsndfile.so.1
libsndfile.so.1.0.28
[/B]

---

### Post by Yellow Pasque on 2018-10-03
Install libsndfile1-dev

---

### Post by ghimes04 on 2018-10-19
Okay, so i tried installing libsndfile 1.0.28 but it still says libsndfile 1.0.2 not found

---

### Post by oldos2er on 2018-10-20
Did you install the *-dev package? That's the one the ./configure script needs.

Which version of Ubuntu are you running?

---

