---
title: "advice for linux mouse event c++ needed"
date: 2007-07-11
forum: Programming Talk
---

### Post by endlessrain on 2007-07-11
is it possible and if so, how can i invoke a mouseclick or displacement through c++ code in linux instead of physically clicking a mouse.  any advice or examples would be much appreciated

thx in advance!

---

### Post by skullmunky on 2007-07-14
yes, you can control the mouse through XWindows.  here's an example, roughly, but you should look up each of these commands to use 'em properly.  XWarpPointer moves the cursor.


Display *display;
Window root;
int x1=0,y1=0;

display=XOpenDisplay(0);
root = XRootWindow(display,0);
XSelectInput(display,root,KeyReleaseMask);

while(1)
{
 x1++;
 y1++;
 XWarpPointer(display, NULL, root, 0, 0, 0, 0, x1, y1);

}


there's a related one for generating clicks, i'm sure.

---

