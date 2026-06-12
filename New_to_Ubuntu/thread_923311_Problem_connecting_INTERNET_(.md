---
title: "Problem connecting INTERNET :("
date: 2008-09-18
forum: New to Ubuntu
---

### Post by deepdhan on 2008-09-18
Hi,
  I have installed Ubuntu, but I dont know how to setup my internet connection. I have broadband connection, it works fine on windows machine. Please let me know how to??

---

### Post by hellion0 on 2008-09-18
Are you behind a router, or do you connect straight to the broadband modem? (Some DSL modems also function as routers)

If you have a router, do you connect wired or wirelessly?

What type of adapter is it? (Manufacturer, model, that stuff.) Some ethernet/wireless adapters are harder to get working under Linux than others.

---

### Post by sh4d0w808 on 2008-09-18
Hello,

If your connection is cable-based and your NIC is known, then U have internet already :) If U have a DSL-connection, U need ppp and pppoe packages and pppoeconf for the configure your connection.

---

### Post by halitech on 2008-09-18
> **sh4d0w808 said:**
> Hello,

If your connection is cable-based and your NIC is known, then U have internet already :) If U have a DSL-connection, U need ppp and pppoe packages and pppoeconf for the configure your connection.

that will depend on the ISP settings, not all are using PPPoE yet

open a terminal and post back the outputs of

```
ifconfig 
```

---

### Post by deepdhan on 2008-09-18
Its a wired connection, I have a ADSL modem.. Its direct connection to Internet. Its a Personal Laptop..  ifconfig i will try and post the output, as m at office , but I really need this working :((

---

### Post by ellalan on 2008-09-18
Hi
[http://packages.ubuntu.com/hardy/allpackages](http://packages.ubuntu.com/hardy/allpackages)

You can download from the link above:
1.libgda3-common
2.libgda3-3
3.libgdl-1-common
4.libgdl-1-0
5.libgdl-gnome-1-0
6.python-gnome2-extras



Install them in that order and use the ADSL modem manager from this link:
[http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page](http://www.squeezedonkey.com/wiki/linux/index.php?title=Main_Page).
HTH.

EDIT: I have just noticed there is a new package for Hardy Heron in the link above([www.squeezedonkey.com](www.squeezedonkey.com)), in that case I don't think you need to download and install the six packages I have mentioned above.

---

