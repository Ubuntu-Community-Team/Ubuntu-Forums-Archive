---
title: "Grab shortcuts for screenlocker"
date: 2008-01-23
forum: Programming Talk
---

### Post by Moezzie on 2008-01-23
Im currently working on a screelocking application under Ubuntu. It basicly puts a window in fullscreen infront of everything else that promts the user to enter his password. 

Its basicly finnished exept for i cant seem to figure out how to disable or grab shortcuts like "alt+tab" and "alt+f4".

Im working with Trolltechs Qt libraries, but they dont seem to offer any features like this. I got a tip about using something called a Keyboard Hook.
I cant really find any useful information on this so im asking you guys. Could you maybe point me in the right direction or even explain a little bit about it?

Thanks for you time.
Moezzie

---

### Post by mssever on 2008-01-23
I don't know much about GUI programming, but I know that xscreensaver works similarly. You might look through its source for some help. I'm guessing that gnome-screensaver is also similar.

Granted, neither xscreensaver nor gnome-screensaver use Qt, but their source might still be useful. (Not that I know anything about Qt.)

---

