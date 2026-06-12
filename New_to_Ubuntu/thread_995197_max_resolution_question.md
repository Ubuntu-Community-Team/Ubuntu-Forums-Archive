---
title: "max resolution question"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by interceptorV8 on 2008-11-27
okay...  to start...

i have a HP a1710n...
nVIDIA 256 MB GeForce 7300 GS 

i dual boot with vista and ubuntu 8.04

previously had two 19" LG monitors hooked up although both only worked with vista, whereas linux did not like using dual monitors with the nvidia card...  when i would enable the restricted drivers and set the visual effects to "extra" the computer would freeze.  because of this i just would unplug one monitor and use the other for linux and use both for vista...  

THE PRESENT:  bought a reconditioned 26" LG (LG  W2600H-PF).  max screen resolution of 1920x1200.  works great w/ vista.  it displays the full resolution, but my scenario w/ linux is that it is restricted to displaying a max res of only 1680x1050.  it's not a HUGE deal, but i'd like to get 1920x1200 in linux as well.

any idea? suggestions?

---

### Post by doyouhas on 2008-11-27
Obvious things include making sure you're using the right nvidia driver.  I assume that you check the screen resolution to make sure it's set as high as possible? It could be capable of displaying higher res but for some reason is not.

---

### Post by kevstar31 on 2008-11-27
Post the output of:
```
cat /etc/X11/xorg.conf
```
You need to open a terminal type the command above and hit enter.

---

### Post by Michael.Godawski on 2008-11-27
Did you try this:

[LIST]
[*][http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Large_Widescreen_Support)
[/LIST]

---

### Post by Kareeser on 2008-11-27
Adding a virtual display to the "Display" SubSection in Xorg.conf seems to be in order...

---

### Post by kevstar31 on 2008-11-27
Try this modline```
Modeline "1920x1200" 185.24  1920 2016 2240 2664  1200 1200 1203 1241 
```[http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1920+1200&FREQ=56-75]("http://http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1920+1200&FREQ=56-75")

---

### Post by interceptorV8 on 2008-11-27
> **Michael.Godawski said:**
> Did you try this:

[LIST]
[*][http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Large_Widescreen_Support)
[/LIST]



i've modified the xorg file...

here's what it looks like (give or take some formatting issues with this):


Section "Device"
	Identifier	"nVidia Corporation G71 [GeForce 7300 GS]"
	Driver		"nv"
	BusID		"PCI:2:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1920x1200" 154 1920 1968 2000 2080 1200 1203 1209 1235
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7300 GS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
EndSection





i've backed-up and modified it and rebooted a few times and so far, nothing :(

---

### Post by kevstar31 on 2008-11-27
> **kevstar31 said:**
> Try this modline```
Modeline "1920x1200" 185.24  1920 2016 2240 2664  1200 1200 1203 1241 
```[http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1920+1200&FREQ=56-75]("http://http://www.bohne-lang.de/spec/linux/modeline/modline.php?MODE=1&RE_VALUE=1920+1200&FREQ=56-75")

Try this modeline instead.

---

### Post by interceptorV8 on 2008-11-27
> **kevstar31 said:**
> Try this modeline instead.

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1920x1200" 185.24  1920 2016 2240 2664  1200 1200 1203 1241
	HorizSync	30-70
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation G71 [GeForce 7300 GS]"
	Monitor		"Generic Monitor"
	DefaultDepth	24


still nothing...

---

### Post by Michael.Godawski on 2008-11-27
Try to reconfigure the x server with:
```
dpkg-reconfigure xserver-xorg
```
 And if you do not want to answer all the questions but only those which are rated with high priority:
 ```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by kevstar31 on 2008-11-27
try these values
> Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Modeline	"1920x1200" 185.24  1920 2016 2240 2664  1200 1200 1203 1241
	HorizSync	30-**83**
	VertRefresh	**56-75**
EndSection


[http://www.pixmania.co.uk/uk/uk/1405435/art/lg/w2600h-pf-26-wide-format.html]("http://www.pixmania.co.uk/uk/uk/1405435/art/lg/w2600h-pf-26-wide-format.html")

---

### Post by interceptorV8 on 2008-11-27
> **kevstar31 said:**
> try these values

[http://www.pixmania.co.uk/uk/uk/1405435/art/lg/w2600h-pf-26-wide-format.html]("http://www.pixmania.co.uk/uk/uk/1405435/art/lg/w2600h-pf-26-wide-format.html")

okay, i have no clue what the hell i just did... i did both of these:
dpkg-reconfigure -phigh xserver-xorg
dpkg-reconfigure xserver-xorg

i rebooted and now the monitor displays 1920x1200..

but here's what it looks like now:

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

_________________________________________________

is this normal though? 

Section "Monitor"
	Identifier	"Configured Monitor" 

should i leave it alone now that it's working?

I read that kevstar31 suggested I make the “monitor” line look like:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Modeline "1920x1200" 185.24 1920 2016 2240 2664 1200 1200 1203 1241
HorizSync 30-83
VertRefresh 56-75
EndSection

---

### Post by interceptorV8 on 2008-11-27
i have to head to another thanksgiving feast gentlemen... i'll be back on later to read more reponses...   in the meantime   THANK YOU EVERYONE for your support and help.  it truly is greatly appreciated :)

---

### Post by Michael.Godawski on 2008-11-27
> okay, i have no clue what the hell i just did... i did both of these:
dpkg-reconfigure -phigh xserver-xorg
dpkg-reconfigure xserver-xorg

i rebooted and now the monitor displays 1920x1200..

That's good news I guess :); you have your resolution and when nothing is exploding then leave a working system unchanged.

---

