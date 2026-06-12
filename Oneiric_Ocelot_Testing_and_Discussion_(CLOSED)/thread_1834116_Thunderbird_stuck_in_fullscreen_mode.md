---
title: "Thunderbird stuck in fullscreen mode?"
date: 2011-08-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2011-08-27
Is anyone else getting Thunderbird always starting fullscreen, with no possibility to resize or drag it around? It even occupies the screen space where my non-hiding launcher bar sits.

---

### Post by ArtLaForge on 2011-08-27
> **MacUntu said:**
> Is anyone else getting Thunderbird always starting fullscreen, with no possibility to resize or drag it around? It even occupies the screen space where my non-hiding launcher bar sits.

Sort of, Thunderbird opens full screen each time, however if I cursor to the top left bar I can minimize and then resize. But I have to do that each time.:confused:

---

### Post by MacUntu on 2011-08-27
Here it is really fullscreen, so no top bar, no window decoration, nothing. Not even Alt+drag works. :-)

---

### Post by JRV on 2011-08-27
Unity automatically maximizes a window when it fills over 75% of the screen. To disable this you need to install compizconfig-settings-manager with the command:

```

sudo apt-get install compizconfig-settings-manager

```

Then run it:
```
ccsm
```

Click on "Ubuntu Unity Plugin"

Click the "Experimental" tab.

Change "Automaximize value" to 100%

A window will also auto maximize if you drag it to the top of the screen. To disable this annoyance uncheck "Grid" in the "Window Management" section of ccsm.

---

### Post by MacUntu on 2011-08-27
Thanks, but that's both not the problem here.

---

