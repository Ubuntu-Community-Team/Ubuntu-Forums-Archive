---
title: "x11 keycodes?"
date: 2008-01-16
forum: Programming Talk
---

### Post by Crenfinkle on 2008-01-16
hi, I'm developing an application using wxPython, but I'm using python-xlib.fake_input to simulate a key event in a target window. What I would like to do is simulate [Ctrl-V] for "paste" if this is possible. I seem to remember reading that [ctrl] modifiers do not have direct keycodes, but I'm definitely not sure. 

Is there a keycode for this combination, or a good resoruce where I can find a chart of all the keycodes? I've googled for hours....

thanks,
Chris Crenshaw

---

### Post by mathisdermaler on 2008-01-16
Try googling for keyboard scan codes instead of "key codes"

I found this which probably has much more detail than you need:

[http://www.win.tue.nl/~aeb/linux/kbd/scancodes-1.html#ss1.5](http://www.win.tue.nl/~aeb/linux/kbd/scancodes-1.html#ss1.5)

It seems unlikely that CTRL+V has its own scancode.  I think either you need to send a CTRL-down scancode followed by V scancode followed by CTRL-up scancode.  

If that isn't how it works, then your API should have a "modifiers" mask.  Typically it would be one byte where 1's bit is left shift, the 2's bit is right shift, 4's bit is ctrl, 8's bit is alt and so on and so forth.

---

### Post by Crenfinkle on 2008-01-16
thank you for helping! I solved the problem by running "xev" and recording the key codes for the relevant keys. Then it worked pretty much like you said, I had to emulate the Ctrl key Press followed by the V key, then Release each in turn. Works like a charm.

thanks again

---

