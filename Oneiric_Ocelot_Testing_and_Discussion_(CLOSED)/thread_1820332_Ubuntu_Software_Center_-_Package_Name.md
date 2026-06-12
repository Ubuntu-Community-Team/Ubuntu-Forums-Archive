---
title: "Ubuntu Software Center - Package Name?"
date: 2011-08-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ShadowMage on 2011-08-07
Hi,

In the Ubuntu Software Center, when looking up an item, the package name and version number was provided in the USC version that comes with Ubuntu 10.04 Lucid Lynx. However, in the USC version that comes with Oneiric Alpha 3, I cannot find this info. The only thing I see is the package names of the available add-ons, but not the name of the package itself that I am viewing. Please see the attached screenshots (the first shows the package version and  name of an item in the USC in Ubuntu 10.04, the other shows the package names of the addons of this item in the USC in Ubuntu 11.10  Alpha 3).

As a user, I would like to know the name of the package before installing it. For example, I may want to install it from the terminal instead of USC, or once installed I may want to run it from the terminal, in order to see any additional info or error messages provided in the terminal that I may be interested in. However, the package name is not displayed in the USC. Am I missing something, or has this feature been taken out? Is this a bug?

Thanks.

---

### Post by terry_gardener on 2011-08-07
it is under the details section

---

### Post by ShadowMage on 2011-08-07
Aha! Thanks, you are right! =)

I'm testing on a live USB and I couldn't find it because it seems I needed to update the "catalog" (sudo apt-get update) after enabling the software source (universe). Before that, the "version" entry didn't display in the details section because the item I was viewing (vlc) was a part of the newly enabled software source (universe).

Thanks again, marking thread as solved :)

---

