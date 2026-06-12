---
title: "what to do when you have no titlebars"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by rickycodie on 2008-04-26
i've had this problem a few different times and it seemed like each time it was a different cause. here are my solutions. this guide assumes that you are running compiz.

1. try using the settings manager (sudo apt-get install compizconfig-settings-manager if you don't have it) and then disable the reflections and the water effects.

2.try setting the way that you want compiz, with the settings manager, and then uninstall it. the settings manager, not compiz.

3. if they only disapear on a certain application, using the settings manager go to the workarounds section and disable the workaround for that application. ( this mainly works for firefox in gutsy.)

4. try installing emerald if you haven't already. ( sudo apt-get install emerald)

5. sometimes it's as simple as changing your titlebar theme.

6. try installing emerald-themes ( i don't know why this works but sometimes it does) ( sudo apt-get install emerald-themes)

7. If you have a nvidia card and if you are using the non-opensource drivers, run this command,```
sudo nvidia-xconfig --add-argb-glx-visuals
```  afterwards save all open work and press ctrl+alt+backspace. this will reset your xserver. thanks to TimJBart

8. and last resort is to edit your xorg.conf
open a terminal and type or paste 

```
sudo gedit /etc/X11/xorg.conf
```

and then if you have a nvidia card add this code to the section that says nvidia, 

```
Option "AddARGBGLXVisuals" "True"
```

so it should look like this:

```
Identifier     "Default Screen"
    Device         "Nvidia GeForce Go 6150"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
```

ensure that the DefaultDepth is set to 24 as well.


if you don't have nvidia then just open a terminal and type in```
sudo gedit /etc/X11/xorg.conf
``` 

add the same code to the screen section
```
Option "AddARGBGLXVisuals" "True"
```

and

```
Option 		"AddARGBGLXVisuals" "True"
```

so it looks similar to this

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Option 		"AddARGBVisuals" "True"
	Option 		"AddARGBGLXVisuals" "True"
EndSection
```

that's everything that i've found that helps. i hope it helps you.

---

