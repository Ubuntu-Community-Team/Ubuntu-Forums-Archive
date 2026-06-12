---
title: "Screen Resolutions"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by reyhan on 2008-04-26
hello i just login to my Ubuntu but why at Login Window
the resolution is so Big?
i usually using 1280 x 1024

---

### Post by BennyHill on 2008-04-26
Hi there,

Open in terminal:-

sudo gedit /etc/X11/xorg.conf

you should have something similar to this, near the bottom:-

Section "Screen"
	Identifier	"Screen0"
	Device		"Videocard0"
	Monitor		"Monitor0"
	Defaultdepth	24
	Option		"TwinView"	"0"
	Option		"metamodes"	"nvidia-auto-select +0+0"
	SubSection "Display"
		Depth	24
		Virtual	1024 768

in the virtual part change what you have there currently to the screen resolution you want and hopefully it works, as it did for me.

---

