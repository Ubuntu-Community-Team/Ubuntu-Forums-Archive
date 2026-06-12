---
title: "Terminal View is cut off"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by thaxtonjl on 2008-08-13
I have a fresh install of Ubuntu 6.06.2 LTS Server on an Averatec laptop and the bottom line or two of the terminal is off the bottom of the screen. How do I adjust the display settings for terminal mode? I'm a total Linux noob, but if someone could just point me in the right direction I think I can figure this out.  Thanks!

---

### Post by ggaaron on 2008-08-13
Have you tried to auto-sync your monitor?

---

### Post by taseedorf on 2008-08-13
You can try at the top editing some of the terminal settings.  Otherwise, if you mean that resolution is too low, try holding ctrl (i think) with the mouse and moving it.  If its not ctrl its something else similar.

---

### Post by Dill on 2008-08-13
Ctrl Shift + should magnify the Terminal display; Ctrl - should demagnify it. I'm not sure if this holds for the Server edition, though.

---

### Post by ggaaron on 2008-08-13
I don't thing that he has X on server. If you don't then you must adjust your monitor settings, not software settings.

---

### Post by thaxtonjl on 2008-08-13
> **ggaaron said:**
> Have you tried to auto-sync your monitor?
Thanks for the replys, but so far no luck.

There is no auto-sync that I know of, just your basic laptop screen with no monitor controls.

Nor is there a mouse since I don't have a GUI installed.

Ctrl -/+ didn't work either.

I've discovered that it is just the bottom line of the console which is off the bottom of the screen.  Is there possibly a way to adjust the number of lines the console displays since it appers to be trying to display one too many?

---

### Post by thaxtonjl on 2008-08-13
> **ggaaron said:**
> Have you tried to auto-sync your monitor?
Thanks for the replys, but so far no luck.

There is no auto-sync that I know of, just your basic laptop screen with no monitor controls.

Nor is there a mouse since I don't have a GUI installed.

Ctrl -/+ didn't work either.

I've discovered that it is just the bottom line of the console which is off the bottom of the screen.  Is there possibly a way to adjust the number of lines the console displays since it appers to be trying to display one too many?

---

### Post by ggaaron on 2008-08-13
O, laptop is another issue... I don't know anything you can do in software with this, console always just worked for me, all tuning had to be done in monitor. As I don't have experience with Ubuntu Server - does it use framebuffer? Usually on laptops you can make them (in bios or by default) not to stretch resolution -  if laptop screen is 1280x800 and you use 640x480 you get only a rectangle in the centre. It might be a solution. 640x480 is default console resolution, you can change it by using a framebuffer.

---

### Post by mali2297 on 2008-08-13
You could try adding a **vga** boot option, see 
[http://ubuntuforums.org/showthread.php?t=258484](http://ubuntuforums.org/showthread.php?t=258484)

---

