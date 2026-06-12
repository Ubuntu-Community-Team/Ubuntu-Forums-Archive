---
title: "[SOLVED] Dual Monitors - Laptop - Intel Graphics"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by trginter on 2008-07-10
I've got a Dell laptop running Ubuntu 8.04.  I want to hook my 19" Widescreen Gateway monitor up to my laptop, either as a 2nd monitor or as the main monitor.  I've tried plugging it in and the Gateway just flashes No Signal.  The laptop has integrated video, Intel i810 I believe.  Anyone know how I can get it to work?

---

### Post by LowSky on 2008-07-10
There should be a key on your keyboard that should switch monitors. Use the Function key (Fn) and one of the F keys for instance, mine is Fn+F7. The key will look like a monitor and a laptop...

---

### Post by trginter on 2008-07-10
On the F8 button it says CRT/LCD.  That's the only function button that comes close.  Tried pressing that and nothing happens.  I find it hard to believe this problem can be solved by a button on my keyboard.

The laptop is a Dell XPS M140.

---

### Post by LowSky on 2008-07-10
well my next idea is for you to hook up the monitor, turn it on, and try to fix your xorg.conf file
boot in to safe mode from grub then type at the prompt
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by trginter on 2008-07-10
> **LowSky said:**
> well my next idea is for you to hook up the monitor, turn it on, and try to fix your xorg.conf file
boot in to safe mode from grub then type at the prompt
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

So I turned the laptop off and then back on and the monitor was recognized and is working.  I was only using ctrl + alt + backspace before, not fully shutting it down I guess.  Sweet!

---

