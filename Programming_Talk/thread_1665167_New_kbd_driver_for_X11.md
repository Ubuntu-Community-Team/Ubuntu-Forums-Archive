---
title: "New kbd driver for X11"
date: 2011-01-11
forum: Programming Talk
---

### Post by worksofcraft on 2011-01-11
I was learning all about x11 input drivers. Then according to this page: [http://www.x.org/wiki/Development/Documentation/XorgInputHOWTO](http://www.x.org/wiki/Development/Documentation/XorgInputHOWTO) it says:

"Note that if you think about writing a new input driver for a "common" device (e.g. touchscreen, mouse, keyboard, etc.), please don't."

I desided I disagree ("typical" I hear you think, but reasons follow) anyway now I'm really wanting to hear opinions of others and you can flame me if you want and I'll try (very hardly) to not take offence... :P

So why would I want to write a new x11 keyboard input driver?

Well it's like this...

Lots and lots of different languages need special "input methods" to generate their wierd and wonderful character codes that they entail, but currently these "methods" are being implemented as part of different (gtk) widgets... IMO that is a really dumb way of doing it. What we want is to for generic system wide "input methods" to generate their "wierd and wonderful" codes and feed them directly into the keyboard driver as if some wierd and wonderful key was pressed.

---

### Post by nvteighen on 2011-01-12
But, isn't it done that way already??

---

### Post by worksofcraft on 2011-01-12
> **nvteighen said:**
> But, isn't it done that way already??

Maybe so, but if it is... how do I get my program to insert pseudo keystrokes into the keyboard buffer so that x11 handles  them as were they genuine key press events?

... conversely, say I do Ctrl-Shift-U 20AC then an € appears in my current text entry, but I never got a € key press event in my application :confused:

Now run a program like xterm and try the same... It doesn't work at all and there are no input methods available what-so-ever!

OTOH, if it *were* going via the keyboard then these facilities would be universally available to all applications, so IMO all the developers are doing atm is adding complexity into specific Gtk widgets instead of enhancing the whole system.

---

### Post by Barrucadu on 2011-01-12
Unless I'm misunderstanding what you're trying to do, X already does this&#8212;have a look at XCompose.

---

### Post by worksofcraft on 2011-01-12
> **Barrucadu said:**
> Unless I'm misunderstanding what you're trying to do, X already does this—have a look at XCompose.

Thanks for that info :)

... I'm totally confused now with SCIM and XIM and IBUS and different keyboard layouts and different compose keys and hidden config files... and environment variables to set and... I think I'll definitely have to write my own after all :shock:

---

