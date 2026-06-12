---
title: "Insert text at keyboard focus with a script"
date: 2010-07-06
forum: Programming Talk
---

### Post by Zorgoth on 2010-07-06
Using Ubuntu/GNOME, how would you insert text at keyboard focus using a script, allowing a keyboard shortcut that would insert text, possibly based on input?

---

### Post by Zorgoth on 2010-07-07
I have solved my original problem to an extent.  I found a virtual keyboard called xvkbd that can input text from the command line, and also am looking into XSendEvent().

However, xvkbd sends my input directly to the window in question rather than through the window manager it seems, so it will not recognize my keyboard shortcuts for performing compiz actions, my right super key for changing keyboard layout while pressed, or my right alt key for third level characters.  How do I make xvkbd actually simulate *exactly* what would happen if I pressed a particular combination of keys?

---

### Post by simosx on 2010-07-07
> **Zorgoth said:**
> I have solved my original problem to an extent.  I found a virtual keyboard called xvkbd that can input text from the command line, and also am looking into XSendEvent().

However, xvkbd sends my input directly to the window in question rather than through the window manager it seems, so it will not recognize my keyboard shortcuts for performing compiz actions, my right super key for changing keyboard layout while pressed, or my right alt key for third level characters.  How do I make xvkbd actually simulate *exactly* what would happen if I pressed a particular combination of keys?

I think the easiest way to do this is to use the Accessibility support in GNOME. You can get a list of windows, select a window and send all sort of (keyboard, in your case) events.

For more, see
[http://live.gnome.org/Accessibility](http://live.gnome.org/Accessibility)
[http://projects.gnome.org/accessibility/](http://projects.gnome.org/accessibility/)
[https://fedorahosted.org/dogtail/](https://fedorahosted.org/dogtail/)

From those, dogtail is actually quite cool; you perform the task once (press keys on the keyboard) and it records the actions into a script. Then, you can edit the script and expand on the code.

---

