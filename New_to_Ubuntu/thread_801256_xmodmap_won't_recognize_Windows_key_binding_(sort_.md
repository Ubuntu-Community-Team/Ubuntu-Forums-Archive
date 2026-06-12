---
title: "xmodmap won't recognize Windows key binding (sort of)"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by txtrbo on 2008-05-20
I'm having an odd problem with xmodmap and the keyboard shortcuts configuration program on my Compaq Presario Notebook.  Even though I have bound the key properly and set the shortcuts, the keys won't do anything (except for Win+M which inverts the screen colors even though it's set to minimize all windows and bring the desktop into focus).

I have followed the [instructions]("https://wiki.ubuntu.com/Lkraider/XmodMap") to set the Windows key (keycode 115 - 0x73) to Super_L and to map that to mod4.  When I run xmodmap it shows mod4 thusly:

```
mod4        Super_L (0x73),  Hyper_L (0x80),  Super_L (0x7f)
```

Using xev, I have not been able to find keycode 127 (0x7f), nor have do I have any listing for that key in my .xmodmap file (or any standard xmodmap file that I've searched).  I am not adding Super_L as 0x7f, xmodmap just does that on its own.


When I run the Keyboard Shortcuts, the program recognizes the Windows key as mod4 (since lock screen shows up as mod4+L), but the Win+L doesn't do anything except maybe cause whatever line that's highlighted to blink once.

I've been fighting this for over a day now.  What am I missing?!

---

### Post by txtrbo on 2008-05-21
One time bump in the hopes that someone, somewhere has encountered this and knows of a fix or what I am doing wrong.

---

