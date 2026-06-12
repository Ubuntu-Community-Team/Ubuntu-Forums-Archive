---
title: "Do I really need to hand code scrolling to track arrow keys in Gtk TextView?"
date: 2008-10-27
forum: Programming Talk
---

### Post by moephan on 2008-10-27
Hello,

I am writing a pyGtk app that place a history of a work item in a TextView. While reading the history, it is naturally to use the arrow keys to scroll down through the history. Upon reaching the bottom of the TextView, the arrow key just merrily sends the cursor off the bottom of the visible region of the TextView, whereas users would expect the TextView to scroll to keep the cursor in view.

It appears that I can hand code this functionality by responding to move-cursor event, but I can't help feeling that I'd be doing it the hard way.

Any thoughts? TIA

Cheers, Rick

---

### Post by nvteighen on 2008-10-27
> **moephan said:**
> Hello,

I am writing a pyGtk app that place a history of a work item in a TextView. While reading the history, it is naturally to use the arrow keys to scroll down through the history. Upon reaching the bottom of the TextView, the arrow key just merrily sends the cursor off the bottom of the visible region of the TextView, whereas users would expect the TextView to scroll to keep the cursor in view.

It appears that I can hand code this functionality by responding to move-cursor event, but I can't help feeling that I'd be doing it the hard way.

Any thoughts? TIA

Cheers, Rick

Forget the scroll bars: GTK+ gives scrolling facilities only when objects are placed inside a GtkScrolledWindow. So, you first create the GtkTextView, then the GtkScrolledWindow using the 'gtk_scrolled_window_add_with_viewport()' function (that's how it's called in C, which as I hope you know is the native language for GTK+... I guess in PyGTK, it should be a method called 'add_with_viewport()'). You need a hidden GtkViewPort to automatize the movements... otherwise you'll have to code scrolling adjustments by hand.

Then, you have to set the GtkScrolledWindow's policy: whether you want a vertical bar, an horizontal or both according to some criteria.

Sadly, I can't show you any code as my experience with GTK+ has always been in C...

---

### Post by moephan on 2008-10-27
Thanks for the help. I guess I should have pointed out that the TextView is inside a ScrolledWindow already, and another way to look at the problem is that the ScrolledWindow does not scroll automatically when the user uses the arrow keys to make the cursor moves out of the viewport.

I'll see what a "hidden" GtkViewPort is, and if that heelp.

Cheers, Rick

---

