---
title: "Gtk ScrolledWindow: autoscroll?"
date: 2009-11-25
forum: Programming Talk
---

### Post by kumoshk on 2009-11-25
Is there any way to set up autoscrolling functions for a ScrolledWindow in Gtk?

I'm programming in Vala, if that makes a difference.

---

### Post by ksprasad on 2009-12-01
Hi,
You can do it using container.
[http://library.gnome.org/devel/gtk/unstable/GtkContainer.html#gtk-container-set-focus-vadjustment](http://library.gnome.org/devel/gtk/unstable/GtkContainer.html#gtk-container-set-focus-vadjustment)

If you want the auto scrolling in a text view,
[http://library.gnome.org/devel/gtk/unstable/GtkTextView.html#gtk-text-view-scroll-to-iter](http://library.gnome.org/devel/gtk/unstable/GtkTextView.html#gtk-text-view-scroll-to-iter)

hope this helps.

Regards,
ksprasad

---

### Post by kumoshk on 2009-12-01
Thanks. That seems it will work for me.

So, I have another question.

I want my autoscrolling to be smooth (i.e. not go by larger chunks). However, I also want it to keep track of which line number corresponds to the upper portion of the TextView. I know how to do it by having it autoscroll a whole line at a time, but I need it to be more gradual than that. I also know how to do it smoothly without keeping track of the line number.

Basically, in read-only mode (without a cursor visible), I use an iterator to make the arrow keys scroll it only and exactly one line at a time (to make it look clean and all). I need to keep track of the line number to do this. So, if I were to autoscroll without keeping track of the line number, then once I used my arrow keys again, it would take me back to the point when autoscrolling started.

I mean, the problem is that I use get_iter_at_line to give the iter a line number, but I don't know how to do that if I'm scrolling by something other than line units (which I would need to to make it smooth).

Now, there is a function that puts the cursor 'somewhere' on the screen, and perhaps I could use that to track the line number somehow, but the problem is, it doesn't let me choose *where* on the screen the cursor will appear (and it's not always the same place).

Do you have any ideas?

---

