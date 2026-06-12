---
title: "Laptop Volume Controls not working in 11.10"
date: 2011-11-26
forum: New to Ubuntu
---

### Post by tehcavil on 2011-11-26
Just upgraded Mint 11 -> Xubuntu 11.10, and it's pretty good except that the laptop volume control keys no longer work. It's just a minor annoyance, but still it would be nice to get them working.

My laptop is an Asus A53U
AMD dual core E350 1.6 GHZ
Radeon HD 6310M / 4 GB memory
500 GB HDD / Xubuntu 11.10/win7 dual boot

I can still change the volume by "clicking" and moving the volume slider but this gets a bit annoying.

Any help you guys could give would be appreciated.

Thanks, Cavil.

---

### Post by tehcavil on 2011-11-26
bump

---

### Post by LewisTM on 2011-11-29
The Xfce volume daemon doesn't support Pulseaudio and doesn't seem to see the volume buttons (or send the right command) on some laptops. 

You have three options (that I know of...)
1. Remove the XFCE volume daemon startup item. Install the GNOME-settings-daemon which will handle the buttons. It must be set at startup as well. Never tried it but it is reported to work.

2. Remove the pulseaudio package. This will leave you with ALSA. Depending on your sound card this may work fine or break sound mixing. Xfce-volumed directly talks to ALSA.

3. Force the use of the buttons — Install asla-utils. In the xfce keyboard shortcuts, add commands bound to the volume buttons:
```
XF86AudioRaiseVolume - amixer set Master 2dB+ unmute
 XF86AudioLowerVolume - amixer set Master 2dB- unmute
 XF86AudioMute - amixer set Master toggle
```

---

### Post by tehcavil on 2011-11-29
thanks! I disabled the xfce volume daemon and installed gnome-settings-daemon to startup, and it works perfectly now!

---

### Post by BlinkinCat on 2011-11-29
Don't forget to mark as "solved" with thread tools at top of page.

---

