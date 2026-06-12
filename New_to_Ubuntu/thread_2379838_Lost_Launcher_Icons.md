---
title: "Lost Launcher Icons"
date: 2017-12-10
forum: New to Ubuntu
---

### Post by perpetuum_mobile2 on 2017-12-10
Dedicated Ubuntu 16.04 LTS desktop.
All launcher icons are gone after the most recent update. Grub-boot in Recovery Mode has the same results. I can create new icons and I can access "All settings" through the mouse buttons.
How can I reload or re-create the launcher icons?

---

### Post by Frogs Hair on 2017-12-10
Can you get a terminal window open with Ctrl+Alt +T or from the right-click context menu on the desktop ?

---

### Post by perpetuum_mobile2 on 2017-12-10
Yes, I can get a terminal window through a mouse right click menu (Ctrl+Alt+T does not work)

---

### Post by Frogs Hair on 2017-12-10
Here are some compiz and unity reset commands. Try the first two and continue if needed. 

Resets Compiz:

```
sudo apt-get install dconf-tools
```

```
dconf reset -f /org/compiz/
```

Resets Icons to defaults:

```
unity --reset-icons
```

Resets Unity:

```
setsid unity
```

---

### Post by perpetuum_mobile2 on 2017-12-13
Thank you for the help. My computer is back to functional mode.
After the "Reset icons to defaults" I allowed the system to reboot. It booted to a completely blank screen, which I am familiar with as this happens most of the time. Then I reboot to the Grub menu into recovery mode, then resume normal boot and everything works at a lower screen res. setting and a bit slower.
Previously I traced my completely blank screen problem to the onboard graphics issue. If I try to do a "Failsafe graphic mode" from the Grub menu, - configure yourself = "not detected" or if default is selected = locks up.
Graphics: Gallium 0.4 on LLVM 3.8 Pipe 128bits. Is there an "easy way" to fix this or I should just keep booting through "Recovery mode"?

---

### Post by Frogs Hair on 2017-12-15
I've not had problems with those drivers . You may want start a thread in hardware including the computer's specs since there's more to this than Unity not stating properly.

---

