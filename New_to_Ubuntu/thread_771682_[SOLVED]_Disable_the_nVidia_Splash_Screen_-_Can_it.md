---
title: "[SOLVED] Disable the nVidia Splash Screen - Can it be done?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by crjackson on 2008-04-27
I have the 169.12 driver installed and working fine.  How in the world can I disable the splash screen.

I tried adding option   NoLogo  True  and option NoLogo 1 but neither of these have an effect.  How can I kill that thing.

Running Hardy btw...

---

### Post by daimaru on 2008-04-27
edit your xorg.conf file:
```
sudo gedit /etc/X11/xorg.conf
```
go to section "Device" and add Option "Nologo"

```
Section "Device"
    Identifier    "nVidia Corporation G80 [GeForce 8800 GTS]"
    Boardname    "nv"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
   [COLOR=Red]** Option          "NoLogo"**[/COLOR]
    Screen    0
EndSection
```

---

### Post by ru7hl3ss on 2008-04-27
It should just be:

```
Option "NoLogo"
```

Here is mine:


```
Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8600M GS]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600M GS"
    Option "NoLogo"
EndSection
```

---

### Post by enigmaniac23 on 2008-04-27
I'm running 8.04.

Here is my xorg section
```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
      EndSection


```

This works for me.  If I change the True to False, then I get the logo.  I've gone back and forth and this is definitely turning the logo on and off for me.

---

