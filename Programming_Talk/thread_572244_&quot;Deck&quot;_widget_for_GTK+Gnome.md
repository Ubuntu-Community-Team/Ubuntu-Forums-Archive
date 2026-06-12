---
title: "&quot;Deck&quot; widget for GTK+/Gnome?"
date: 2007-10-10
forum: Programming Talk
---

### Post by yodermk on 2007-10-10
Hi, I want to write a "hosted" trivia type program (will be GPL).  The idea is that the "host" with a laptop operates the GUI on the laptop screen, while an external monitor/projector displays what is visible to the participants.

The external screen should contain a fullscreen window that can quickly flip between displays.  For example, one display might have the current scores, one might have the question with optional choices, one might be a canvas, and one might display photos.

In programming Firefox/XUL, there is a <deck> element that would do this nicely.  You can programatically change the widget that is currently on top and being displayed.  But I didn't seem to see one in GTK+ after browsing through the Glade interface builder and the documentation.

Does one exist?  If not, how might you do it?

I'm pretty sure I want to do this application in Python using the GTK/Gnome bindings, building it with Glade.  I might be open to other tools though.

Thanks!

---

### Post by archivator on 2007-10-10
I would simply keep an array of pointers(references) to the different widgets and iterate throught it. When the user requests a different widget, an iterator would be increased/decreased accordingly, the current window would be hidden and the iterator's window will be shown.

If you can't grasp it, I can write some sample code (you haven't specified a language btw).

---

### Post by yodermk on 2007-10-10
Ok, thanks.  So can I have a list of arbitrary widgets such as a couple VBOXes, a canvas, and maybe others, then call gtk_widget_show and gtk_widget_hide on them?  When a widget is hidden, it takes no space, right?  And how would they be packed into the container window?

Or would I have to do it on a whole-window basis?  I'm not sure that would work well, partly due to flicker, and partly because the new window might pop up on the wrong screen.  (Right now, the only way I can think of doing it is opening a window, telling the user to drag it to the external display, and calling gtk_window_fullscreen on it.)

BTW I did specify that I was hoping to do it in Python with Glade.

Thanks!

---

