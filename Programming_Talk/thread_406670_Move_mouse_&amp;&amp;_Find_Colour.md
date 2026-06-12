---
title: "Move mouse &amp;&amp; Find Colour"
date: 2007-04-11
forum: Programming Talk
---

### Post by Darkness3477 on 2007-04-11
Hi, I've been searching around google for a fair while now, and am yet to find how to both move the mouse, the detect whether a certain colour is displayed on the screen. 

The closest thing I have found to be being able to move the mouse is this
```
from ctypes import *
windll.user32.SetCursorPos(100, 100)
```

But, as you'll notice, it's for windows, which isn't exactly going to help me at all. :D

Now, it's not too important that I find out how to do this, as I know how to do it using C++ (found a tutorial for it, yay!) but I'd rather do it in Python. Actually, if I don't figure out how to do it it doesn't matter to much, i was just interested in doing this. 

Anyway, if you guys could provide a link to some documentation that'll tell me how to move the mouse, and find a colour on screen (and then returns the hex code of the colour to a variable), or provide a quick example I'd be very greatful. 

As always, thank you very much for any and all help you guys are able to give

Michael

---

