---
title: "Unity panel service still eating RAM like mad?"
date: 2011-08-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-08-09
[IMG]http://img.xrmb2.net/images/775165.png[/IMG]

580 MB after 2 1/2 days - sounds awesome! :D

Compiz with 270 MB isn't too shabby either. At least prices for memory are super low at the moment, maybe it's a conspiracy? :D

Here's a bug report: [https://bugs.launchpad.net/ubuntu/+source/unity/+bug/801709](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/801709)

---

### Post by dino99 on 2011-08-09
dont forget to add libgtk-3.so and python2.7 issues to the borked system ;)

Thats how bleeding-edge/testing is :)

---

### Post by LADmaticCA on 2011-08-09
How do you get your htop to display RES in MB?

---

### Post by mc4man on 2011-08-09
> **LADmaticCA said:**
> How do you get your htop to display RES in MB?
Wait till the value(s) hit 100MB

---

### Post by MacUntu on 2011-08-09
IIRC you can also highlight the MB part of the <100MB entries, but I don't like that much.

---

### Post by mc4man on 2011-08-09
> **MacUntu said:**
> IIRC you can also highlight the MB part of the <100MB entries, but I don't like that much.

That seems to be the default here, though I guess can be turned off/on in F2
(also switches over here around 97 or so.

There is a new general purpose leak bug (doesn't include unity panel yet
[https://bugs.launchpad.net/unity/+bug/813365](https://bugs.launchpad.net/unity/+bug/813365)

---

### Post by mc4man on 2011-09-09
This newer bug, (also from MacUntu) seems to be one of the worst current mem leaks in O
[https://bugs.launchpad.net/unity/+bug/835646](https://bugs.launchpad.net/unity/+bug/835646)
What's interesting is that natty had/has the same issue. While it did get a 'fix released' in natty it actually was never really fixed, the numbers are just reduced from it's highpoint (and certainly less than whats currently seen in O

If one has a lot of mem and or doesn't stay online for extended time then maybe not a big deal, otherwise it can be.
(if affected and not having an particular love of the 'global menu' then removing appmenu* will greatly reduce the mem leak in u-p-s

---

### Post by MacUntu on 2011-09-10
I'd say, if you have 1 GiB of RAM you'll start using swap within a couple of hours. With 4 GiB I couldn't run the system for a week without swapping (resident memory, not cache!). Unfortunately the information I provided wasn't too helpful (no obvious thing standing out in the valgrind log).

It definitely got something to do with application menus - the more/bigger menus the application has, the bigger the leakage is.

Eg., run this simple python app and watch the mem usage of unity-panel-service before and after using it: [http://paste.ubuntu.com/686288/](http://paste.ubuntu.com/686288/) It's creating 100 menus with 50 entries each, adding 65 MiB to the u-p-s process.

---

### Post by mc4man on 2011-09-14
The latest on this certainly isn't encouraging (other than this has to be fixed or at least reduced ala natty

---

### Post by MacUntu on 2011-09-14
Hehe, even worse for Unity-2D users that are also facing this new funny leak: [https://bugs.launchpad.net/unity-2d/+bug/850320](https://bugs.launchpad.net/unity-2d/+bug/850320)

The ocelot needs some new o-rings. :D

---

### Post by aura7 on 2011-09-14
Use Gnome Classic if the problem still persists

---

### Post by MacUntu on 2011-09-14
Uhm, no, I'd rather kill unity-panel-service every couple of hours than using that crappy GNOME fallback session. :)

---

