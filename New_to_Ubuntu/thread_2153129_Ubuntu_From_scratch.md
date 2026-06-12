---
title: "Ubuntu From scratch"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by dayab on 2013-06-10
Hello everybody, I am trying to create ubuntu from scratch, using debootstrap following the tutorials, [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch). It only talks about the LIVE CD. Live CD works perfectly well. Could we add text based installer, that is used in ubuntu server in the debootstrap base system and make our own installable verison of ubuntu.

Thanks

---

### Post by Frogs Hair on 2013-06-10
Hello and Welcome

The following is the minimal CD and has a text based/CLI  installer, but I'm not sure if that is what you are looking for.      [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by VMC on 2013-06-10
> **dayab said:**
> Hello everybody, I am trying to create ubuntu from scratch, using debootstrap following the tutorials, [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch). It only talks about the LIVE CD. Live CD works perfectly well. Could we add text based installer, that is used in ubuntu server in the debootstrap base system and make our own installable verison of ubuntu.

Thanks

Maybe [InstallCDCustomization]("https://help.ubuntu.com/community/InstallCDCustomization") is what your looking for. See item #2 there.

---

### Post by Cheesehead on 2013-06-10
> **dayab said:**
> Hello everybody, I am trying to create ubuntu from scratch, using debootstrap ... Could we add text based installer, that is used in ubuntu server in the debootstrap base system and make our own installable verison of ubuntu?

No.
Debootstrap, the (Live) GUI installer, and the (mini/server) text-based installer are three *different* ways to install. Trying to mix them will only result in tremendous frustration for you.

Pick one way to install. Since you say you want to use debootstrap, use only debootstrap for this install and ignore the others. 
If you follow the instructions carefully, debootstrap is safe and not difficult.
Once you reach the point of a working package manager on your new system, it's easy and familiar.

There *is* a text-based selector used in the server installer that you can safely reuse. It's the 'tasksel' package, and it's not an installer - just another package manager front-end.

---

