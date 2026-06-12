---
title: "Login screen runs at lower resolution?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Muffinabus on 2008-05-28
I was fiddling with my graphics card drivers yesterday, and I must've done something because now my login screen runs at a lower resolution than my desktop.  It fixes itself when I login, but it looks terrible on my LCD screen when it doesn't run at the native resolution.

Anyone have an idea on how to fix it?

---

### Post by Muffinabus on 2008-05-28
/tear  Anyone /:?

---

### Post by iaculallad on 2008-05-28
> **Muffinabus said:**
> /tear  Anyone /:?

You could post your /etc/X11/xorg.conf (**cat /etc/X11/xorg.conf**) file for members to check or you could try looking at this [link]("http://ubuntuforums.org/showthread.php?t=807451") for resolution problem.

---

### Post by akiratheoni on 2008-05-28
I had this problem too. I don't know if it's the fix for you because we might have different video cards (I have an Intel GMA 950).

I fixed it though by adding this to my Monitor section of the xorg.conf:

> 	Option "PreferredMode" "1680x1050" 

So mine looks like:

> Section "Monitor"
	Identifier	"LCM-22w3"
	Option		"DPMS"
	HorizSync	30-82
	VertRefresh	56-76
	Option "PreferredMode" "1680x1050" 
EndSection

Of course, change the 1680x1050 to your resolution.

---

### Post by Primefalcon on 2008-05-28
do the 

```
sudo displayconfig-gtk
```

just to make sure the xorg file is properly filled, the less you have to fill out with it manualy the better....

then go into the xorg file 

```
sudo gedit /etc/X11/xorg.conf
```

under this section

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1024	768
```

just change the virtual to what you want such as

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	800	600
```

that should solve you login screen resolution

---

### Post by Muffinabus on 2008-05-28
Cool, thanks for the replies guys, seems to be working, for now (;

---

