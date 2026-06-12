---
title: "help??"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by lolpenguin on 2011-10-14
I've just upgraded to oneiric (which took two days due to my computer crashing in between and having to restore). I had used Unity without any problems (sans having to boot into safe mode to upgrade without crashes) and now, when I try to boot into Ubuntu (Unity 3D) the window manager DOES NOT load. What? I checked my proprietary drivers, and yes, it was activated. So for now I'm stuck on Unity 2D (which takes nearly a minute to load). I will update this post if GNOME Shell works.
EDIT: gnome-shell works perfectly
EDIT2: ran ```
/usr/lib/nux/unity_support_test -p
``` and got yes for all

---

### Post by jtarin on 2011-10-14
It sounds as if you could have hardware problems. Do you dual boot with Windows? Do you have problems in that operating system also?

---

### Post by wildmanne39 on 2011-10-14
Hi, I have mine working but I had to use the old driver for my nvidia card just like I did in 11.04, but I am close to having it the way I want it now, and it is working good.

---

### Post by collisionystm on 2011-10-14
> **wildmanne39 said:**
> Hi, I have mine working but I had to use the old driver for my nvidia card just like I did in 11.04, but I am close to having it the way I want it now, and it is working good.

Lucky!

I swear I will never touch another AMD product again.

I am sticking with Intel.

---

### Post by wildmanne39 on 2011-10-14
Hi, I have used an amd processor and nvidia card for several years without any problems, but I do not try to run a new nvidia card like the optimus that would just be asking for trouble.

But I do understand sometimes it is difficult to get everything working the way you want it.
Thank you

---

### Post by madjr on 2011-10-14
> **lolpenguin said:**
> I've just upgraded to oneiric (which took two days due to my computer crashing in between and having to restore). I had used Unity without any problems (sans having to boot into safe mode to upgrade without crashes) and now, when I try to boot into Ubuntu (Unity 3D) the window manager DOES NOT load. What? I checked my proprietary drivers, and yes, it was activated. So for now I'm stuck on Unity 2D (which takes nearly a minute to load). I will update this post if GNOME Shell works.
EDIT: gnome-shell works perfectly
EDIT2: ran ```
/usr/lib/nux/unity_support_test -p
``` and got yes for all

yeah upgrading, have been problematic recently, specially with unity 3d...

can you also send this error to launchpad from 11.10 so they can check/fix the upgrade process and possibly also hand a solution:

in a terminal type and follow instructions:

```
ubuntu-bug unity
```

---

### Post by lolpenguin on 2011-10-14
Well, as it seems, Unity suddenly started working (I found out when I accidentally switched to Unity in root terminal [I was tweaking Unity 2D])
Yes, I am using a dual-boot setup, and in my former natty system, it would occasionally white/grey screen for absolutely no reason.
Thanks for the quick replies anyway.

---

### Post by wildmanne39 on 2011-10-14
Hi, the white/grey screen is because ubuntu has programs running that are taking a little longer then usual to get done so it shows that color to let you know.

It could also mean the program is not working properly or if you are seeing it a lot there maybe a problem otherwise nothing to worry about.
Thank you

---

