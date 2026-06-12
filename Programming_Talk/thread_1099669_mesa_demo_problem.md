---
title: "mesa demo problem"
date: 2009-03-18
forum: Programming Talk
---

### Post by dcrwls-02 on 2009-03-18
I have compiled successfully the mesa demo programs.  However, when I attempt to execute them I see the following behavior.

The main display area displays as it should including any moving object.  The window frame (sizing borders & title window) do not display.  When I try to resize or move the window by placing the mouse where it should be the correct action occurs.  I can close the window by clicking where the close button would be in the title window.

When the application closes it does not erase itself but moving any other application over the area causes the erase.

Can anyone give me some idea what is going on?

---

### Post by Zugzwang on 2009-03-18
Try a different window manager.

Select Preferences->Appearance from the menu and set "Visual effects" to "None". Then start your program again. If it now works correctly, it's not a problem with your program. That's the most likely cause.

---

### Post by dcrwls-02 on 2009-03-18
Thank you that solved the problem.  Do you know if this is this the required mode for all opengl applications or can they be written to function in the "Normal" mode?

---

### Post by Zugzwang on 2009-03-18
> **dcrwls-02 said:**
> Thank you that solved the problem.  Do you know if this is this the required mode for all opengl applications or can they be written to function in the "Normal" mode?

As far as I know, that is a bug with the more fancy window manager "compiz". Hopefully it will be solved one day. As far as I know, full screen applications do not have problems with this. Also, you might find workarounds (what you are basically asking for) on the web.

---

