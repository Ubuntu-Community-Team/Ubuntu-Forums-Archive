---
title: "increase mouse scrolling speed ?"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by smooth3006 on 2008-08-20
how can i adjust my scrolling speed on my mouse from within ubuntu ? you know to scroll web pages faster.

---

### Post by bhadotia on 2008-08-20
Easy:)  go to System>Preferences>Mouse.

---

### Post by fedex1993 on 2008-08-20
go to System>Preferences>Mouse or scroll faster :P

---

### Post by eizzer on 2008-08-20
For now, I don't know if this is possibe with Gnome, but
IIRC with KDE there is option for this.

If you are using Firefox or any browser with same engine
(e.g. Epiphany) you may want to try open "about:config"
and change the value of "mousewheel.withnokey.numlines".

---

### Post by cdtech on 2008-08-20
xset m 3 4

Make the 3 smaller if it is too fast.

**Update::.**
"xset m default" returns it to the standard setting.

---

### Post by Northsider on 2008-08-20
For me, configuring the mouse speed in the preferences menu didn't help much when using firefox.  I had to go to about:config in firefox and find mousewheel (mousewheel.withnokey?)options.

---

### Post by smooth3006 on 2008-08-20
i hate messing with firefox settings unless i have too. i checked the mouse config in ubuntu and theres no option to increase scrolling speed.

---

### Post by cdtech on 2008-08-20
# VertScrollDelta and  HorizScrollDelta is an integer   
# value defining scrolling speed. Smaller values result in  
# faster scrolling.  
Option  "VertScrollDelta"  "100"

Goes in your /etc/X11/xorg.conf under Section "InputDevice", subection Identifier "XXXX" where XXXX is your device.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"  "true"
        **[COLOR="DarkRed"]Option      "VertScrollDelta" "6"[/COLOR]**
EndSection
```

**Update::.**
Used the wrong option line, updated to ZAxis. I just tried this option on mine to see if it would work. I did try the Vert style (6 being the number of lines to scroll)

---

### Post by eizzer on 2008-08-21
> **cdtech said:**
> # VertScrollDelta and  HorizScrollDelta is an integer   
# value defining scrolling speed. Smaller values result in  
# faster scrolling.  
Option  "VertScrollDelta"  "100"

Goes in your /etc/X11/xorg.conf under Section "InputDevice", subection Identifier "XXXX" where XXXX is your device.

```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Emulate3Buttons"  "true"
        **[COLOR="DarkRed"]Option      "VertScrollDelta" "6"[/COLOR]**
EndSection
```

**Update::.**
Used the wrong option line, updated to ZAxis. I just tried this option on mine to see if it would work. I did try the Vert style (6 being the number of lines to scroll)

Isn't that options only apply to synaptic driver?

---

