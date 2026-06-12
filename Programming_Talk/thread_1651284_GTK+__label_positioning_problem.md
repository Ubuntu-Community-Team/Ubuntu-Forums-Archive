---
title: "GTK+  label positioning problem"
date: 2010-12-22
forum: Programming Talk
---

### Post by solaris235 on 2010-12-22
Hey all, I have a frustrating problem. This should be a simple thing to do.
I'm developing a custom GUI for a CNC controller (which really doesn't matter)
The controller window is part of  larger app but needs full focus when active so I have it in a modal top level transparent window.
The main gui element are drawn directly to this window through cairo (cause it looks cool)
For convenience I want to add 3 label to display the x y and z coordinates of the CNC machine. it's easier to update the labels from the hardware thread than draw the updates.
So...
I add a fixed container. (no problem)
I add a label formatted with pango markup. Set it to have a window so cairo doesn't draw over it and fixed_put it to location x=0 y=0 (no problem, looks great the label is 100 pixels wide by 20 pixels high)
Here's the problem. I want the label at x=100 y=50, so I fixed_put it to 100,50 and all I get is a white box with no text in it.
After play around for hours I move the label to x=50 y=0 and what do I see. a box that is 100 pixels wide, 20 pixels high, the left half is all white, the right half shows the first part of my text.(the left half of the formatted text)
As it turns out if I move the label 'x' pixels from  zero relative to the origin of the fixed container the displayed text also moves 'x' pixels but relative to the new label window location offsetting it from the window mapped to the fixed container by a distance of 2x pixels. It does the same when moved in the y direction.
Anyone know why it does this ?
Anyone know how to fix this ?
It does this with buttons as well

(If I have to I can just draw the display text directly but that will give me problems crossing threads with some of the gdk functions. although the app doesn't crash completely it does stop rendering the display which is a whole other problem best left for another thread.)
here are some snippets
```

      w_fixed = gtk_fixed_new();
      gtk_container_add(GTK_CONTAINER(w_cnc),w_fixed);
      gtk_widget_show(w_fixed);

      w_xpos = gtk_label_new("Label");
      gtk_widget_set_has_window(w_xpos,TRUE);
      gtk_widget_modify_fg(w_xpos,GTK_STATE_NORMAL,&gcolor_frame);
      markup = g_markup_printf_escaped ("<span font_desc='14' background = '#161B2E'><b>%s</b></span>", cnc_xpos);
      gtk_label_set_markup (GTK_LABEL (w_xpos), markup);
      gtk_fixed_put(GTK_FIXED(w_fixed),w_xpos,0,0);
      gtk_widget_show(w_xpos);

```This work perfectly until I try to relocate the w_xpos label

---

