---
title: "[GTK] change scrollbar color"
date: 2009-08-09
forum: Programming Talk
---

### Post by tigrezno on 2009-08-09
Is there a way to change the background color of a scrollbar?

I'm doing a fullscreen multi-file monitor, this is like several terminals (textviews) running tail -f at the same time without decorations

When all textviews have the scrollbars, the thing becomes ugly, so I wanted to change the scrollbar color.

Or, can I hide those scrollbars? So, I can scroll with the mouse wheel

---

### Post by SledgeHammer_999 on 2009-08-09
are you putting the textviews into GtkScrolledWindows? If yes try to set the policy to GTK_POLICY_NEVER with [gtk_scrolled_window_set_policy ()](http://library.gnome.org/devel/gtk/stable/GtkScrolledWindow.html#gtk-scrolled-window-set-policy)

---

### Post by tigrezno on 2009-08-09
> **SledgeHammer_999 said:**
> are you putting the textviews into GtkScrolledWindows? If yes try to set the policy to GTK_POLICY_NEVER with [gtk_scrolled_window_set_policy ()](http://library.gnome.org/devel/gtk/stable/GtkScrolledWindow.html#gtk-scrolled-window-set-policy)

I tried, but then the textviews oversized all over the place

---

### Post by Siljrath on 2009-09-19
hi, 
i hope yas dont think i'm hijacking this thread...

i too want to know how to change the colours of the gtk scrollbars, ideally without having to change the bg[normal] thus changing all my nice drk grey.


from orford.org/gtk :> 
scrollbars and scales:

    * use widget_class "*Scrollbar*"to select scrollbars.
    * arrow button and main draggable rectangle colour is controlled by bg[NORMAL]
    * background trough and border is controlled by bg[ACTIVE] (this appears not to be true for the Clear engine)
    * mouseover colour uses bg[PRELIGHT]
    * arrow colour uses fg[NORMAL] n thats for gtk1.2 iirc... so idk if it's even capable of what i seek.  and i dont yet know how to impliment this (would be easier if the theme i'm starting from (simple) would at least have something about it's scrollbars in the themerc.

i've barely begun learning C, let alone gtk and it's widgets n stuff...  but i really want to be able to change the colour of the scrollbar so i can see it in bright sunlight on my laptop.

i'll be continuing to look into how to do this from time to time, but so far its been dead slow progress on this relatively minor issue.

---

### Post by kumoshk on 2009-12-08
I want to know, too.

This is what I've tried, but it hasn't worked:
```
this.myScrolledWindow.get_vscrollbar().modify_base(Gtk.StateType.NORMAL, this.mybgcolor);
```

Anyway, I mostly want it for full screen mode (I'd love to be able to hide them without removing their functionality, as well). For my program, I like to have a black background to keep out all the brightness. However, the scrollbars are rather bright. I know I can change my theme, but this isn't just about me, and I like my theme (the scrollbars are fine everywhere else). Keep in mind, I'll make the color change optional (so it doesn't *have* to mess with anyone's theme).

---

### Post by dannymichel on 2010-05-05
hope i dont get in trouble for bumping

---

### Post by Bill Cosby on 2010-11-04
This is really bugging me.
How come it is such a difficult task, it is ridiculous.
If you use GTK+ themes, you can only access the scrollbar itself with

class "GtkScrollbar"

the background of the scrollbar is a GtkWindow (at least in Firefox), and if I use this to color it, all other widgets using GtkWindow will be in the same color as well.

I haven't found any solution to just color the background of the scrollbar, does really no one know?

regards,
Bill

---

