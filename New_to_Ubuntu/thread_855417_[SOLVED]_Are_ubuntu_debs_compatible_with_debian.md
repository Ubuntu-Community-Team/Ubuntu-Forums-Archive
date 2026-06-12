---
title: "[SOLVED] Are ubuntu debs compatible with debian?"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-10
Can i use debs from ubuntu on debian? Should i?

---

### Post by mojoman on 2008-07-10
> **cristo-father said:**
> Can i use debs from ubuntu on debian? Should i?

You can (usually). You shouldn't (usually). Use debs compiled for ubuntu instead. Maintaining the integrity of the system minimizes the risk of breaking things.

---

### Post by cristo-father on 2008-07-10
> **mojoman said:**
> You can (usually). You shouldn't (usually). Use debs compiled for ubuntu instead. Maintaining the integrity of the system minimizes the risk of breaking things.

But will it break what the deb installs or more than that?

---

### Post by blazercist on 2008-07-10
nah the worst thing that can happen is that the deb doesnt install properly, the only real difference between debian and ubuntu are kernel modifications and packages, i mean you COULD break something but probably not, anyway, anything thats in ubuntu repos should be in the debian repos so you shouldnt have to do what you are asking anyway.

---

### Post by bobbocanfly on 2008-07-19
Ubuntu isnt built to be binary compatible with Debian (we rebuild all packages we sync) but 90% of the time nothing should break too badly. Downloading Ubuntu source packages and building them on Debian should solve any problem (but requires a bit of knowledge).

---

