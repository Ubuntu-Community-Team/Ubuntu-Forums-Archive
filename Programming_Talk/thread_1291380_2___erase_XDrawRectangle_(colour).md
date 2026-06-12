---
title: "2 ?? : erase XDrawRectangle (colour?)?"
date: 2009-10-14
forum: Programming Talk
---

### Post by zlatkart on 2009-10-14
Hi all
1. I use this code to draw on the root window, but somehow i can't work out how to erase this. 
2. Is there an easy way to use colours for XDraw...

```
Display *dpy = XOpenDisplay(NULL);
Window win=XDefaultRootWindow(dpy);
XMapWindow(dpy,win );
int blackColor = BlackPixel(dpy, DefaultScreen(dpy));
GC gc = XCreateGC(dpy,win, 0, NULL);
XSetForeground(dpy, gc, blackColor);
XSetSubwindowMode(dpy, gc, IncludeInferiors);
XDrawRectangle(dpy, win, gc, 0,0, 100,100);  
XFlush(dpy);
XCloseDisplay(dpy);

```

---

### Post by Marco A on 2009-10-14
.

---

### Post by zlatkart on 2009-10-15
> You can draw your rectangle in green (or any colour, just make the change) like this;Thank you for this!

> If I understand correctly, you want to draw the rectangle and erase to leave screen as it was.Yes. 

> Perhaps using two colours and taking the exclusive OR of the two to create another "colour" which will reverse either one of the first two colours by setting the function in the gc to GXxor.

I've not been successful with this yet.
ooh nooo

---

### Post by zlatkart on 2009-10-17
Now I had a lot fun with GXinvert, GXxor...(XFillRectangle over the whole screen), but I want to draw overlapping rectangles, so any of these functions clears the half of my drawings.
Still waiting for a suggestion how to clear the root window.

---

