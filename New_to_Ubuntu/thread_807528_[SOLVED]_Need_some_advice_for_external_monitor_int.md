---
title: "[SOLVED] Need some advice for external monitor intel GM965"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Bill magee on 2008-05-25
I am running Hardy and I love it. I mean can you even compare it to Vista in the same sentence? But my next computer will be tailored to run it, and in part that means no intel GM965.

I am trying to get my external monitor working, and I think I just need a little advice. I have tried figuring the screen resolution setting under preferences, and it sees my Samsung 1280 x 1024 60hz monitor. But when I set prefs and reboot the Samsung comes alive until I enter gnome, then it dies and the laptop screen comes alive, but at the wrong resolution. Then I remove the external monitor, reboot, and all is well with the laptop again.

Below is my xorg. Can anyone give me some advice or point me to a Hardy-specific how-to on the 965?

```

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
	InputDevice	"Synaptics Touchpad"
EndSection

```

Many thanks for these great forums and a great OS.

---

### Post by Bill magee on 2008-05-25
Solved my external monitor problem by restarting X with a ctr-alt-backspace instead of rebooting Ubuntu entirely. 

Noticed that it did not write any data to xorg.conf. Where does Hardy keep monitor and screen data? Anybody know?

Cheers,
Bill

---

