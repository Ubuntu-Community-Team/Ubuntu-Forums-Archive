---
title: "Tcl/Tk: Border Visible Around Canvas Widgets"
date: 2008-07-30
forum: Programming Talk
---

### Post by 3370318 on 2008-07-30
I'm writing an Tcl/Tk script which places a canvas and text widget next to each other.  Due to some of the colors used in the text, a black background provides the best contrast so I decided to make both the canvas and text backgrounds black (along with the parent frame of both).  However, this has revealed an annoying problem that I can't seem to resolve...  there is a border around the canvas widget that I can't remove.

I've tried explicitly setting the x and y padding to 0, flattening the relief, and setting the borders to 0 but nothing has helped.  The border is only about a pixel wide so its just enough to completely destroy the continuity between the canvas and text widgets.

Interestingly enough, I had the same problem with the text widget, but focusing on the text (either in code or by the user) removed the text's border; removing the focus from the text brings the border back.  This method has not worked for the canvas, however.

Has anybody else experienced this problem or found a solution?  I would prefer to use either the pack or grid manager instead of trying to manually place the widgets so any suggestions that don't involve overlapping the two widgets would be preferable.  By the way, I'm using Tcl 8.4 on Linux (Ubuntu and Redhat) and AIX.

Thanks

---

### Post by stevescripts on 2008-07-31
configure your widgets with -highlightthickness 0

Steve

---

### Post by 3370318 on 2008-07-31
Thanks so much for pointing that out.  That option made all the difference...  can't believe I didn't see it before.

---

