---
title: "Flashplugin installer 64-bit wants to install 32-bit libs"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-09-24
On a 64-bit install, flash was working yesterday but today all sites say I have no flash plugin (did some updates in between).

Now when I go to try to install flash, it wants to install around 60 i386 packages.
Is this something to do with the multi-arch thing?

Another oneiric install still has flash installed and working (except in firefox) with no 32-bit libs

---

### Post by Enigmapond on 2011-09-24
Do you also have noscript addon in FF? That could be the cause. Also I would install the Flash-Aid addon to firefox and run the script. You can either install the stable or beta version and it will uninstall any conflicts.

---

### Post by thatguruguy on 2011-09-24
Even better, consider using the sevenmachines ppa for 64-bit flash: [clicky]("https://launchpad.net/%7Esevenmachines/+archive/flash").

---

### Post by x-shaney-x on 2011-09-24
Well as it turns out, the other computer with working flash DOES have the 32-bit libs, I just never noticed them getting installed at any point.

So I went ahead and just installed flashplugin-installer.

I may just try the PPA instead though.

---

### Post by sammiev on 2011-09-24
+1 for Flash-Aid. It really seems to help a lot of people with problems like yourself. :)

---

