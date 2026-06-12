---
title: "Getting X windows keycode from a character in C?"
date: 2008-11-17
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-17
I know xev, but how can I get Xwindows keycode from character in my C program?
Like getting the keycodes on the fly, while program is running.

Will I have to do the hard way, use xev, and do **#define character keycode** for each character?

Or is there possibly an easier way to check keycode for a single character?

---

### Post by nanotube on 2008-11-17
> **crazyfuturamanoob said:**
> I know xev, but how can I get Xwindows keycode from character in my C program?
Like getting the keycodes on the fly, while program is running.

Will I have to do the hard way, use xev, and do **#define character keycode** for each character?

Or is there possibly an easier way to check keycode for a single character?

you can probably use the xlib library api to convert keycode to character. maybe see here:
[http://tronche.com/gui/x/xlib/input/keyboard-encoding.html](http://tronche.com/gui/x/xlib/input/keyboard-encoding.html)

---

### Post by crazyfuturamanoob on 2008-11-17
> **nanotube said:**
> you can probably use the xlib library api to convert keycode to character. maybe see here:
[http://tronche.com/gui/x/xlib/input/keyboard-encoding.html](http://tronche.com/gui/x/xlib/input/keyboard-encoding.html)

No. I want to convert a character to keycode. And without xev, I want to do it on the fly when the program is running.

Like ask a character from user, then get the keycode matching the given character.

---

### Post by nanotube on 2008-11-17
> **crazyfuturamanoob said:**
> No. I want to convert a character to keycode. And without xev, I want to do it on the fly when the program is running.

Like ask a character from user, then get the keycode matching the given character.

i think you can do character->keycode with xlib just as well as keycode->character.

---

