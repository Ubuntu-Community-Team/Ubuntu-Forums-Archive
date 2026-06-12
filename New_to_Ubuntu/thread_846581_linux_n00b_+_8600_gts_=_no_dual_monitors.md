---
title: "linux n00b + 8600 gts = no dual monitors"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by deathvalleyjoker on 2008-07-01
I have an 8600 gts nvidia card. when i installed ubuntu i was happy to see that nvidia supports linux automatically. 

during install, image was cloned on both screens. 

somewhere after installing compiz, the nvidia diver, and going to System-Preferences-Visual Effects, and clicking Extra, the second monitor is not reconized. 

i did some searching in the forums, and couldn't find somthing that looked like it would work. 

[http://ubuntuforums.org/showthread.php?t=845855&highlight=dual+monitors](http://ubuntuforums.org/showthread.php?t=845855&highlight=dual+monitors)

this link looked like it would help the most, but my xorg.config file doesnt looks smilar.

i was also wondering how the cube effect, and multiple desktops works when u run dual monitors.

thanks, mike c.

---

### Post by Law506 on 2008-07-01
I am assuming your using 8.04 correct?

Have you tried running the nvidia-settings tool?

Open a terminal and type **nvidia-settings** and a window should pop up with video card properties.

might sudo nvidia-settings, cant remember off the top of my head, been a bit since I messed with my 8600GTS, moving to 8.04 solved virtually every issue I have had with my card.

---

### Post by deathvalleyjoker on 2008-07-01
Here is my xorg.conf file (also as a forum thing, how do i put a file txt within a window within a post)

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by deathvalleyjoker on 2008-07-01
yes 8.04 AMD X64

---

### Post by PinkFloyd102489 on 2008-07-01
nvidia-settings needs to be installed by the way, it's not a default package. And you need to use sudo with it.

---

### Post by deathvalleyjoker on 2008-07-01
also, my monitors are dell ultrasharp FP 1907(2) 

in the xorg.conf it  states:
Section "Monitor"
Identifier "Configured Monitor"
EndSection

i dont know why it doesnt reconize it. 

finally, the screen resolution says 1080 x 1024, but my firefox window takes up alot more room than it did on XP, jsut to have the yahoo homepage fit. so i dont even know where to begin with that.

---

### Post by deathvalleyjoker on 2008-07-01
Wow! ok thanks pinkfloyd!

wish they would have included that with the driver, but whatever.

---

