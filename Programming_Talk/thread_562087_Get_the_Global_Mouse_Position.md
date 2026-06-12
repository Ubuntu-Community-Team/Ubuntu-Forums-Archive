---
title: "Get the Global Mouse Position"
date: 2007-09-28
forum: Programming Talk
---

### Post by Kenobi on 2007-09-28
Hi,

is there a simple API-Function that can retrieve the mouse position on the whole screen? I tried an SDL-Function but it only works within an SDL-Window, but I need the Mouse Position for any window.

---

### Post by gnusci on 2007-09-28
Try with allegro:

[http://www.talula.demon.co.uk/allegro/](http://www.talula.demon.co.uk/allegro/)
[http://alleg.sourceforge.net/stabledocs/en/alleg004.html](http://alleg.sourceforge.net/stabledocs/en/alleg004.html)

---

### Post by Kenobi on 2007-09-28
Will allegro create new dependencies for my program (in case I want to run it on a foreign machine, will it require allegro to be installed)?

Still, there must be a straight-forward way!

---

### Post by Compyx on 2007-09-28
> **Kenobi said:**
> Will allegro create new dependencies for my program (in case I want to run it on a foreign machine, will it require allegro to be installed)?

Yes, unless you statically link Allegro with your binary which will probably lead to a rather large executable.

> Still, there must be a straight-forward way!

Perhaps you could look into Xlib? XQueryPointer() seems to do what you want.
There's a fairly large chance people have Xlib installed when they use a mouse.

---

### Post by gnusci on 2007-09-28
So use Xlib I also think is good enough if you just only need the mouse coordinates:

[http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html](http://users.actcom.co.il/~choo/lupg/tutorials/xlib-programming/xlib-programming.html)

---

### Post by Kenobi on 2007-09-29
I found that XLib function. It returns quite a useful bunch of things, but it needs a *display pointer. I tried to create one by using XOpenDisplay, but then XQueryPointer hangs up the program. Is there a way to get the *display of the actual screen I'm looking on?

I don't understand why they have to make it that hard. Also I think there could be a GTK-way to get the Mouse Coordinates?

---

### Post by cwcentral on 2008-01-10
Here ya go:


  Display *dsp = XOpenDisplay( NULL );
  if( !dsp ){ return 1; }

  int screenNumber = DefaultScreen(dsp);

  XEvent event;

  /* get info about current pointer position */
  XQueryPointer(dsp, RootWindow(dsp, DefaultScreen(dsp)),
    &event.xbutton.root, &event.xbutton.window,
    &event.xbutton.x_root, &event.xbutton.y_root,
    &event.xbutton.x, &event.xbutton.y,
    &event.xbutton.state);

  printf("Mouse Coordinates: %d %d\n", event.xbutton.x, event.xbutton.y);

  XCloseDisplay( dsp );

---

