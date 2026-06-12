---
title: "Invalid UTF-8 on user switcher"
date: 2011-08-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by oc666 on 2011-08-30
Hey All
I'm getting "Invalid UTF-8" on the user switcher.
See attached file

Thanks in advance

---

### Post by dino99 on 2011-08-30
is your system updated ? Should have been fixed few days ago.

---

### Post by kansasnoob on 2011-08-30
[https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/836587](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/836587)

Maybe :confused:

---

### Post by coffeecat on 2011-08-30
> **kansasnoob said:**
> [https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/836587](https://bugs.launchpad.net/ubuntu/+source/unity-2d/+bug/836587)

Maybe :confused:

No, I think it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137)

Or maybe they're related. :)

> **dino99 said:**
> is your system updated ? Should have been fixed few days ago.

+1.

I saw this and then it autofixed itself with an update.

---

### Post by kansasnoob on 2011-08-30
> **coffeecat said:**
> No, I think it's this bug:

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/834137)

Or maybe they're related. :)



+1.

I saw this and then it autofixed itself with an update.

It's borked with the current iso-testing images, but it's also inconsistent. I'd guess I see it about 2 out of 3, or 3 out of 4 times that I boot the live desktop. Never (so far) with an installed image, and only with Unity-2D.

Does that make sense :confused:

---

### Post by entonjackson on 2011-09-20
No. It doesn't.
It occurs after changing users uid and/or gid.

---

