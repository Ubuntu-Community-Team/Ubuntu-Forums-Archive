---
title: "[SOLVED] scrolling through screen buffer"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by LRT on 2008-06-04
i'm using ubuntu server edition. i have no desktop environment installed. i am just using command line interface. i want to be able to scroll up to screens that have already scrolled past. 

is this at all possible in command line interface?

---

### Post by lfaraone on 2008-06-04
Two options:
Try "CTRL+SHIFT+PAGEUP"

Or sudo apt-get install screen, and run screen. 
Once inside screen, type "CTRL+A" followed by "[", and use pAGEUP/PAGEDOWN. Press ESC to exit screen-copy mode.
[Read more about screen.]("http://www.kuro5hin.org/story/2004/3/9/16838/14935")

---

### Post by LRT on 2008-06-04
actually it wasn't ctrl+shift+pagegup, it was shift+pageup. i never heard of 'screen'. it looks very useful thanks for pointing that out, im going to try it out.

i got one more question though... (and maybe i should post a new thread). while in command line interface is there any utility that i could use to access a web browser without installing a gui??? i've heard of lynx, but i want something graphical without having to install a full blown desktop environment.

---

### Post by lfaraone on 2008-06-04
Try [Ratposion]("http://www.nongnu.org/ratpoison/") which is a _very_ lightweight graphical interface, along with firefox or dillo.

---

### Post by LRT on 2008-06-05
thank you i will give it a try (the keyboard gallery was fascinating!)

---

### Post by LRT on 2008-06-05
ok ratpoison is awesome! thanks for pointing it out to me. i have one question however. i installed firefox (dillo really wasn't rendering the pages correctly, not even google homepage which is very basic) but to open a new tab in firefox the shortcut key is Ctrl+t which is the same for the ratpoison shortcut key to manage the windows. so when i'm in firefox and i hit Ctrl+t the command is taken by ratpoison not firefox... does that make sense? how do i fix this???

---

### Post by LRT on 2008-06-05
figured it out... while in firefox if i type Ctrl+t it will be interpreted by ratpoison but if i type Ctrl+t+t firefox will open a new tab

---

### Post by vedavrata on 2010-03-17
> **lfaraone said:**
> Two options:
Try "CTRL+SHIFT+PAGEUP"

Or sudo apt-get install screen, and run screen. 
Once inside screen, type "CTRL+A" followed by "[", and use pAGEUP/PAGEDOWN. Press ESC to exit screen-copy mode.

Yes, i have the similair necessity to scroll in console (command line interface -- Ctrl-Alt-F1..F6)... 
**Shift-PageUp** / **Shift-PageDown** work but don't scroll output of text application (altough sometimes it scrolls a line).

So, for now, only solution is *'screen'* (terminal multiplexer) - run *screen* (or an application in *screen*) and press **Ctrl+A** then **[** ...
[https://help.ubuntu.com/community/Screen]("https://help.ubuntu.com/community/Screen")

---

