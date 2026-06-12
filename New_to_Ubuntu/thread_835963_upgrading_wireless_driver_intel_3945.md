---
title: "upgrading wireless driver intel 3945"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by analoog on 2008-06-21
running kernel 2.6.24-19-generic (hardy).
I'm currently using a iwlwifi driver if i'm correct.
how can I check the current version number of my driver for my wireless network adapter? 
I think I use a driver from [http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads](http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads)

And is it worth to upgrade to a newer version?
With this driver for example I cannot set my wireless card in monitor mode and I would also like a better receiving range (distance).


:)

---

### Post by sdennie on 2008-06-21
You can check the version with:

```

modinfo iwl3945

```

The page you linked to has updated drivers via [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download) but, I don't recommend installing them unless you look through the change logs and see that the exact changes you want have been implemented.

---

