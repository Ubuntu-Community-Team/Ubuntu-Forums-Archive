---
title: "HOW-TO: Turkish layout problem"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by humanity_to_others on 2005-10-15
If you can't use your Alt gr button, you must change your xorg.conf to below configuration:
```
...
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"tr"
EndSection
...
```

---

### Post by KuradiLammas on 2006-03-18
It works quite fine, thanks a lot 8) 

For editing xorg.conf in English version of Ubuntu:
Lunch term&#305;nal: Applications/Accessories/Terminal
than: 
sudo gedit /etc/X11/xorg.conf
and than find and edit the following lines on above and save.

after it press control+alt+backspace

while gnome opens, click accept X's layout 

And: &#286;Ü &#287;ü  @ &#305;&#304; Çç Öö &#350;&#351; !

---

