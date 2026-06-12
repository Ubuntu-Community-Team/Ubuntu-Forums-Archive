---
title: "Automatically resizing widgets in gtk2"
date: 2009-09-10
forum: Programming Talk
---

### Post by flightless bird on 2009-09-10
I'm trying to teach myself gtk2 gui programming via the medium of perl and gtk2-perl - and so far I'm rather enjoying it. However I'm a bit stuck at the moment and would a appreciate a few pointers:

I have set up a treeview in a scrolled window and that all works perfectly well, and the window rezes well and responds to input and everything. When I manually resize the window however the scrolled window (and thus the treeview) does not expand to fill the newly created space. How can I persuade it to do so?

.glade file and perl code attached.

Many thanks

FB

---

### Post by SledgeHammer_999 on 2009-09-10
I didn't read your code(I don't know perl)... but in what container did you put your treeview widget? Try putting it in a Hbox or Vbox. Then add that container to the scrolled window.

---

### Post by flightless bird on 2009-09-10
Didn't work I'm afraid - it resizes horizontally, but not vertically, as before. Adding a vbox prevented the scrolled window from adding scrollbars too.

---

### Post by haTem on 2009-09-10
You have to change your packing hierarchy a bit. You want to group the widgets based on how you want them to react to resize. I see three groups you would want... the top portion of widgets you probably want to stay the same size (no vertical stretching), that's one group. Then there's the scrolled window + treeview which you want to stretch vertically, that's another group. Then there are the buttons along the bottom which I assume you also don't want to stretch vertically, which is the third group.

Change your root vbox so that is has 3 spaces, one for each group. 

In the first space, pack the message/slider/label widgets in a vbox as you are doing now. Make sure the scrolled window isn't in this vbox: it's not part of this group! Set the vbox to not "expand" or "fill" (under packing in glade).

In the second space, create a hbox and pack in the scrolled window and treeview. Make sure the hbox and scrolled window are set to "expand" and "fill" under packing.

In the last space, create a hbox as you are doing now containing the bottom row of buttons. Set it to not "expand" or "fill". That's it, should work now! If you're still having trouble, I can post the modified glade file, but hopefully my explanation made sense.

---

