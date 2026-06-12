---
title: "How do I adjust the screen brightness in Xfce?"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by nick32665 on 2013-01-28
Help I'm trying to adjust my screen laptop but it is not working.  I'm using an HP laptop if that makes it more helpful.Please help.

---

### Post by Idaho Dan on 2013-01-28
Hey Nick,
if this is a stupid question please disregard.
Did you try the function button on the keyboard.
That's all I have to do on this old HP laptop.
[mine is fn + f8]

Thanks, Dan.

---

### Post by Bucky Ball on 2013-01-28
Applications icon>Settings Manager>Desktop. There is a slider at the bottom of the window.

---

### Post by ACubed10 on 2013-01-28
also if you are trying the buttons on your keyboard to make the screen brighter, I believe that requires you to install a graphics card driver!


just saw this literally 2 seconds ago on another part of the forums [http://ubuntuforums.org/showthread.php?t=2080301](http://ubuntuforums.org/showthread.php?t=2080301)

---

### Post by Impavidus on 2013-01-29
On my HP laptop the brightness keys (Fn+{F2,F3}) work without installing any drivers, but that might depend on your graphics chip (although I don't think that screen backlight is controlled by your graphics). Otherwise you can put the xfce4-brightness-plugin on the xfce panel. It's in the package xfce4-goodies. It allows you to change brightness with the mouse.

---

### Post by Bucky Ball on 2013-01-29
As I mentioned ...

> **Bucky Ball said:**
> Applications>Settings Manager>Desktop. There is a slider at the bottom of the window.

...

---

### Post by nick32665 on 2013-01-29
> **Idaho Dan said:**
> Hey Nick,
if this is a stupid question please disregard.
Did you try the function button on the keyboard.
That's all I have to do on this old HP laptop.
[mine is fn + f8]

Thanks, Dan.
I tried this my button is the f2 and f8 an brightness meter comes up but it does not do anything when I try to change it.

---

### Post by slickymaster on 2013-01-29
There is a XFCE4 plugin that lets you increase the brightness of the monitor easily.
To install it just type at a terminal window:
```
sudo apt-get install xfce4-power-manager-plugins
```
After installation just right-click with the mouse on the top panel. Then navogate to Panel >> add new items, and search for "Brightness Plugin".
The plugin will appear in the upper right, so you can easily adjust the brightness of your monitor.

---

