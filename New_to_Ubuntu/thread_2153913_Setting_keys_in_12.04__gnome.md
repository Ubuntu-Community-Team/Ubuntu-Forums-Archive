---
title: "Setting keys in 12.04 / gnome"
date: 2013-06-12
forum: New to Ubuntu
---

### Post by Stunt Double on 2013-06-12
I added Character Palette to my panel, and then used Character Map to create useful palettes. I need to program  key combinations so I can enter some of the characters without pasting them from the palette. The application I'm using won't accept the pasted characters.
    How do I program a combination of keys to directly enter the needed characters from the palette?
Thanks

---

### Post by Isamu715 on 2013-06-15
What characters exactly do you want entered? You can try using *xdotool*(install it from the Software Center). With *xdotool* installed set a keyboard shortcut to:
```
xdotool type --delay 0 xx
```
Replace *xx *with whatever symbol you want entered.

---

