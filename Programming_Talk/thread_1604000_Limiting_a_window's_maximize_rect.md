---
title: "Limiting a window's maximize rect"
date: 2010-10-23
forum: Programming Talk
---

### Post by rg4w on 2010-10-23
I'm porting an app to Linux that's currently running on Win and OS X, and the app has multiple windows for various views with one floating window which is a toolbar we position at the top of the display.

With Mac and Win we can use their APIs to set a limit on the size of a window when the user clicks the Maximize button, so the result places the window along the left, right, and bottom of the display but the top is just below the toolbar.

We've been trying to turn up an API for Gnome which would allow us to define the maximize bounds, but my lead tells me there is no such thing.

We have long-term plans to migrate the multi-window UI into a single window divided into panes, so after we implement that next year we won't have this challenge at all.

But we have some university customers who'd like us to deliver our Linux version ASAP, and we have the budget to do so but I'm concerned that the current maximize behavior makes it too easy to have the view windows submarine beneath the toolbar, obscuring the controls which would let them restore the original rect of the window.

Is there an API somewhere that we've overlooked which would enable us to do this?

So far the only workaround we can come up with is to resize the window back down after maximize, but that's ugly of course and I'd like our Linux version to be as attractive as we can make it.

Thanks in advance for any tips you can offer.

---

### Post by Zugzwang on 2010-10-23
So QT seems to have functionality for limiting a window's size: the "maximumSize" property of a QFrame (inherited from QWidget). Perhaps you can have a look at the source code and see how they implemented this feature?

---

### Post by rg4w on 2010-10-23
Thanks for the lead - I'll check it out.

---

### Post by nvteighen on 2010-10-24
Hm... I'm not sure, but this may be related to the Window Manager, rather than the GUI toolkit library.

---

### Post by Vox754 on 2010-10-24
> **nvteighen said:**
> Hm... I'm not sure, but this may be related to the Window Manager, rather than the GUI toolkit library.
The toolkit communicates with the window manager in some way.

Try this example with Tk:
```

vocx@UB:~$ tclsh
% package require Tk
8.5.8
% wm geometry . 600x600
% wm maxsize . 300 300
% wm geometry . 600x600
% # use the mouse to resize

```

That's right, the basic Tcl shell does not use GNU readline!

---

