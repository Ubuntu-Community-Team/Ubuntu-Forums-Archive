---
title: "Mesa upgraded to 7.11"
date: 2011-06-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-06-29
Mesa is just getting upgraded to the version 7.11 in Oneiric repos.
Two new packages are added:
- libgbm1
- libglapi-mesa

Here:
[https://launchpad.net/ubuntu/oneiric/+source/mesa/7.11~1-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/mesa/7.11~1-0ubuntu2)

Works OK.
Just remember that proprietary drivers need to get reinstalled after mesa update.
Otherwise 3D is gone.

---

### Post by martine.ginette on 2011-07-07
Is it possible to perform the upgrade under 11.04?

Martin.

---

### Post by cariboo on 2011-07-07
> **martin.genet said:**
> Is it possible to perform the upgrade under 11.04?

Martin.

The short answer no, as you won't have the rest of the dependencies. You only need a small 10GiB partition to test Oneiric.

---

### Post by Yellow Pasque on 2011-07-08
> **martin.genet said:**
> Is it possible to perform the upgrade under 11.04?

Martin.
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

