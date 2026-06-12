---
title: "[Python/TK] Turn Key 2D Graphing Solution"
date: 2007-08-03
forum: Programming Talk
---

### Post by xtacocorex on 2007-08-03
Just curious if anyone knows of a turn key (pre-built OSS) graphing app in Python using TK?  If not, does anyone have tutorials or something to give me direction in where/how to proceed.  I need to plot x & y coordinates as they are being updated in real time.

Thanks for any/all help.

---

### Post by cwaldbieser on 2007-08-03
> **xtacocorex said:**
> Just curious if anyone knows of a turn key (pre-built OSS) graphing app in Python using TK?  If not, does anyone have tutorials or something to give me direction in where/how to proceed.  I need to plot x & y coordinates as they are being updated in real time.

Thanks for any/all help.

I'm not sure where you can find any tutorials, but you definitely could use the canvas widget to plot some lines.

---

### Post by braddcadd on 2007-08-03
[http://www.serpia.org/pygtk](http://www.serpia.org/pygtk)

Not sure if that module is a turn-key solution or not, but I think it is an up an coming module.

HTH

---

### Post by xtacocorex on 2007-08-03
Thanks cwaldbieser, I'll look into the canvas widget.  Didn't know what it was called.

I do need to stick to TK since I need it cross platform without having to install dependencies on Windows.

---

### Post by xtacocorex on 2007-08-06
The canvas widget will work, but is there a way I could have a point move while the window is open? 
 
I'm generating a random x & y coordinate for each point within the window range, creating a small rectangle to be a point and need those to move along a pre-defined path.  Can this be done?  All the stuff I've seen requires the mainloop() and I don't know if you are able to modify the data while it's in mainloop().  Is there where threads come in?

---

### Post by cwaldbieser on 2007-08-07
> **xtacocorex said:**
> The canvas widget will work, but is there a way I could have a point move while the window is open? 
 
I'm generating a random x & y coordinate for each point within the window range, creating a small rectangle to be a point and need those to move along a pre-defined path.  Can this be done?  All the stuff I've seen requires the mainloop() and I don't know if you are able to modify the data while it's in mainloop().  Is there where threads come in?

Look into the following methods that are defined on most widgets:
after
after_idle
after_cancel
update
update_idletasks
wait_variable
wait_window
wait_visibility

The after() and update() methods are probably the most useful.

The last time I checked, only the main thread can manipulate the GUI in Tkinter (this seems to be a common theme in a lot of GUI toolkits).

---

