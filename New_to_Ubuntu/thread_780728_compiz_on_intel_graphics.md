---
title: "compiz on intel graphics"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Kenn on 2008-05-03
before hardy heron gusty ran nice and smooth on intel chipset. Now after hardy installed firefox scrolling is choppy and stuttery + games run at a snails pace.

---

### Post by damis648 on 2008-05-03
Have you tried installing the restricted drivers? (if there are any?)

PS: does the scrolling look like waves just moving up the window? if it does that means a wrong driver

---

### Post by Kenn on 2008-05-03
yep so where do i get these restricted drivers

---

### Post by damis648 on 2008-05-03
Try System>Administration>Hardware Drivers in the panel and click the check box on your graphics card (if it is in there)

EDIT: WHOA that had to be the longest string of two letter words starting with I in history

---

### Post by Kenn on 2008-05-03
"No proprietary drivers....."
there's nothing there

---

### Post by damis648 on 2008-05-03
Hm... what is the model of your card?

---

### Post by Kenn on 2008-05-03
i think its 945gm intel family chipset thing

---

### Post by Helios38 on 2008-05-03
thats a bit weak 4 compiz.


go into preferences > appearance > visual effects


and click none


some stuff will happen, your desktop will dissapear for a few secs

and compiz will be off. things should speed up.

---

### Post by damis648 on 2008-05-03
ok try going into terminal and typing
```
gedit /ext/X11/xorg.conf
```
and find the section that starts like this:
```
Section "Device"
    Identifier  "Intel Corporation Mobile 945GM"

```
and tell me what the next line down says, the line that says "driver"

EDIT: it is a bit weak, however we should not see this scrolling issue if it using the correct driver, however i have never used this specific card so i am not positive.

---

### Post by Whiffle on 2008-05-03
Do

"glxinfo | grep direct"

If it replies something about Direct Rendering: Yes, then you're pretty much set to have compiz work.  I have it working on my 915GM and its not too shabby.

---

### Post by m_ad on 2008-05-03
How did you get your intel graphics to work with compiz in Gutsy? I have..

Intel Corporation Mobile GM965/GL960 Integrated Graphics

and I can't get compiz to work with it. Says I'm blacklisted.

---

### Post by adult swim on 2008-05-03
to the OP, i have the same intel card and was having this problem.  by adding a couple things to my xorg.conf it worked itself out. 
if you hit alt-f2 and then type in gksudo gedit /etc/X11/xorg.conf and press enter, go down to where it says section "Device" and at the end of that section, add the following ```
Option 		"AccelMethod" 		"EXA"
Option 		"MigrationHeuristic" 	"greedy"
``` then save the file, log out of ubuntu and then log back in. things should go alot smoother!

---

### Post by Kenn on 2008-05-04
tried what you said adult swim no change at all

@damis648
```
Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
	Option 		"AccelMethod" 		"EXA"
	Option 		"MigrationHeuristic" 	"greedy"
EndSection
```

---

