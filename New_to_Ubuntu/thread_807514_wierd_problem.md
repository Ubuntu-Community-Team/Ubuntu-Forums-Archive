---
title: "wierd problem"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by r5gtt2k3 on 2008-05-25
Ok so i took the plunge and went from 7.10 x86 to 8.04 x64 and all is fine untill i goto setting up my dual screens, Now with 7.10 i had both screens as dualview, but when i maximized windows they maximizes to just 1 screen (which ever screen the windows were on at the time of maximizing)

But now, It maximizes across both the screens making the windows really big, Does anyone know why I'm getting this ? and know how to make it back to normal ?

Oh I'm also using a Nvidia 8600GT

---

### Post by r5gtt2k3 on 2008-05-25
Using NVIDIA x Server settings, I think i have chose every option in there and it either gives me only 1 screen or makes them both into 1 screen (i don't want a clone) I want it like ultramon does to windows if you know what i mean

---

### Post by r5gtt2k3 on 2008-05-26
Can it not be fixed ? Why does Ubuntu not have an option to make it how i would like it :confused:

---

### Post by BasiliusCarver on 2008-08-02
I think it will be that xinerama could be on. try editing your xorg.conf file (sudo gedit /etc/X11/xorg.conf) and adding:

```
Section "ServerFlags"
    Option         "Xinerama" "false"
EndSection
```

e.g (this is the last part of my xorg.conf file):

```
Section "ServerLayout"
	Identifier	"Dual1"
  screen "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "ServerFlags"
    Option         "Xinerama" "false"
EndSection
```

Remember when typing in the gedit command that the file location part is case-sensitive.

---

