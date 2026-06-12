---
title: "Xorg can't load graphics driver"
date: 2015-08-24
forum: New to Ubuntu
---

### Post by jason_gibson2 on 2015-08-24
14.04.3 LTS Server version.

*EDIT* Solved, I'm an idiot and didn't think to check which driver I was installing. I thought the radeon one was the driver, now that i did ati it works great...

```
[   510.857] Loading extension GLX
[   510.857] (==) Matched fglrx as autoconfigured driver 0
[   510.857] (==) Matched ati as autoconfigured driver 1
[   510.857] (==) Matched fglrx as autoconfigured driver 2
[   510.857] (==) Matched ati as autoconfigured driver 3
[   510.857] (==) Matched modesetting as autoconfigured driver 4
[   510.857] (==) Matched fbdev as autoconfigured driver 5
[   510.857] (==) Matched vesa as autoconfigured driver 6
[   510.857] (==) Assigned the driver to the xf86ConfigLayout
[   510.857] (II) LoadModule: "fglrx"
[   510.858] (WW) Warning, couldn't open module fglrx
[   510.858] (II) UnloadModule: "fglrx"
[   510.858] (II) Unloading fglrx
[   510.858] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   510.858] (II) LoadModule: "ati"
[   510.858] (WW) Warning, couldn't open module ati
[   510.858] (II) UnloadModule: "ati"
[   510.858] (II) Unloading ati
[   510.858] (EE) Failed to load module "ati" (module does not exist, 0)
[   510.858] (II) LoadModule: "modesetting"
[   510.859] (WW) Warning, couldn't open module modesetting
[   510.859] (II) UnloadModule: "modesetting"
[   510.859] (II) Unloading modesetting
[   510.859] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   510.859] (II) LoadModule: "fbdev"
[   510.859] (WW) Warning, couldn't open module fbdev
[   510.859] (II) UnloadModule: "fbdev"
[   510.859] (II) Unloading fbdev
[   510.859] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   510.859] (II) LoadModule: "vesa"
[   510.860] (WW) Warning, couldn't open module vesa
[   510.860] (II) UnloadModule: "vesa"
[   510.860] (II) Unloading vesa
[   510.860] (EE) Failed to load module "vesa" (module does not exist, 0)
[   510.860] (==) Matched fglrx as autoconfigured driver 0
[   510.860] (==) Matched ati as autoconfigured driver 1
[   510.860] (==) Matched fglrx as autoconfigured driver 2
[   510.860] (==) Matched ati as autoconfigured driver 3
[   510.860] (==) Matched modesetting as autoconfigured driver 4
[   510.860] (==) Matched fbdev as autoconfigured driver 5
[   510.860] (==) Matched vesa as autoconfigured driver 6
[   510.860] (==) Assigned the driver to the xf86ConfigLayout
[   510.860] (II) LoadModule: "fglrx"
[   510.860] (WW) Warning, couldn't open module fglrx
[   510.860] (II) UnloadModule: "fglrx"
[   510.860] (II) Unloading fglrx
[   510.860] (EE) Failed to load module "fglrx" (module does not exist, 0)
[   510.860] (II) LoadModule: "ati"
[   510.861] (WW) Warning, couldn't open module ati
[   510.861] (II) UnloadModule: "ati"
[   510.861] (II) Unloading ati
[   510.861] (EE) Failed to load module "ati" (module does not exist, 0)
[   510.861] (II) LoadModule: "modesetting"
[   510.861] (WW) Warning, couldn't open module modesetting
[   510.861] (II) UnloadModule: "modesetting"
[   510.861] (II) Unloading modesetting
[   510.861] (EE) Failed to load module "modesetting" (module does not exist, 0)
[   510.861] (II) LoadModule: "fbdev"
[   510.862] (WW) Warning, couldn't open module fbdev
[   510.862] (II) UnloadModule: "fbdev"
[   510.862] (II) Unloading fbdev
[   510.862] (EE) Failed to load module "fbdev" (module does not exist, 0)
[   510.862] (II) LoadModule: "vesa"
[   510.862] (WW) Warning, couldn't open module vesa
[   510.862] (II) UnloadModule: "vesa"
[   510.862] (II) Unloading vesa
[   510.862] (EE) Failed to load module "vesa" (module does not exist, 0)
[   510.862] (EE) No drivers available.
[   510.862] (EE) 
Fatal server error:
[   510.862] (EE) no screens found(EE) 
[   510.862] (EE) 
Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
[   510.862] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   510.862] (EE) 
jason@micromachine:~$
```

---

### Post by Yellow Pasque on 2015-08-25
Please mark your thread solved.

FWIW, radeon is the actual driver (ati is just a wrapper). However, Xorg's autodetect looks for "ati" so it also works with pre-Radeon cards that don't use the radeon driver.

---

