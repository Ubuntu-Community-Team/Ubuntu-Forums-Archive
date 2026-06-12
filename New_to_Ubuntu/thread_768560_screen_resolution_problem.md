---
title: "screen resolution problem"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by uthturn on 2008-04-26
I just installed 8.04 and I cannot get my screen resolution above 640*480 In 7.10 i had it running at 1680-1050 . I have the restricted drivers installed and I've tried editing my xorg.cong whick i'm posting below

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
(my edit)SubSection "Display" (I added this subsection)
        Depth        24
        Modes      "1680x1050_50.00"
    EndSubSection(End of my edit)
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by Qwerty_ on 2008-04-26
Try reconfiguring your xserver.

```
 sudo dpkg-reconfigure xserver-xorg
```

---

### Post by uthturn on 2008-04-26
wow thats weird resolution is now at 800x600

---

### Post by Qwerty_ on 2008-04-26
When you went through and reconfigured the xserver with the above command did you select the resolution to be 1680X1050?

---

### Post by uthturn on 2008-04-26
it just asked keyboard stuff never said anything about resolution

---

### Post by ghost_ryder35 on 2008-04-26
thats weird, run the command again. You can always try to change the resolotuin by going to System, Prefrences, Screen Resolution or editing the xorg.conf file (probally not the best idea :))

---

### Post by Qwerty_ on 2008-04-26
Hmm thats odd that should of let you set your drivers and then set your resolutions I guess something must of changed in Hardy.

---

### Post by uthturn on 2008-04-26
when i go there to change it the highest res is 800*600 and says cloned output and the clone screens option is checked i've tried unchecking it but it is checked when i open screen resolutions again

---

### Post by uthturn on 2008-04-26
heres what my xorg.conf looks like
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
EndSection

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

---

### Post by uthturn on 2008-04-26
damn when i restarted it reset the resolution back to 640*480 . I tried the reconfig command but it doesn't ask anything after keyboard variant and says this in the term 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080426105544

---

### Post by hariprs on 2008-04-26
I was also facing the same problem. I uninstalled the nvidia drivers and downloaded the latest drivers from nvidia site and installed it. Then everything works fine.

---

### Post by Zralou on 2008-04-26
> dpkg-reconfigure xserver-xorg
From what i've experienced using Hardy as Beta, the above command doesn't work anymore.  When you got 800x600 you had reset back to 'vista' drivers.

I had the same problem when I first installed Hardy, what I did eventually was download EnvyNG (make sure you get the 'NG' version for Hardy) and let it install the nvidia driver, then I searched google for my monitor refresh rates, then I manually edited the xorg.conf file with the correct monitor settings.

Sara Lou

---

### Post by uthturn on 2008-04-26
reinstalling the drivers fixed the problem thanks all:)

---

