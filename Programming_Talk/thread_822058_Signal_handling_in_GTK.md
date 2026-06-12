---
title: "Signal handling in GTK"
date: 2008-06-07
forum: Programming Talk
---

### Post by Vadi on 2008-06-07
My sample GTK setup is as follows: I have a GtkHandleBox, inside it a GtkToolbar, and several GtkToggleToolButtons inside it. Here's what I'd like to accomplish - when the user right-clicks on the area that the handlebox covers, show a menu. Even if the right-click was on a button (and in this case the button should not go off).

Here's how I thought I'd accomplish this - attach a callback function to the button-pressed signal to my gtkhandlebox. If the click is a right-click, show my menu and whatnot, and stop the signal propagation. If it's not a right-click, let it go on, so that the buttons get pressed properly.

But this isn't working, as it seems the button is getting the signal before me, handling it, and not propagating it.

I'm suspecting that I'd need to disconnect the button's handler for the button-press event, and add my own in, that if it's a right-click, does nothing and propagates the event. Would this be the 'right' way to do it? I'm still quite new to GTK.

---

### Post by MicahCarrick on 2008-06-09
You may just want to connect a handler to the "popup-context-menu" signal of the GtkToolbar.

---

### Post by Vadi on 2008-06-09
Unfortunately, that does not work - when the mouse if over the buttons, they steal my signal anyway.

I've attached a modified tutorial example to show you.

---

### Post by MicahCarrick on 2008-06-09
Okay, I did a little test and although not "easy", it works. 

A GtkToolButton is derived from GtkToolItem which is derived from GtkContainer. Peaking at the source for GtkToolButton, I see that it simply packs a GtkButton into itself. So, if we can get that GtkButton then we could connect to that button's "button-press-event". A GtkToolButton does not give you direct access to it's child GtkButton, however, we can use GtkContainer's functions to do so.

You can:

1. Get each GtkToolButton using gtk_builder_get_object()
2. Get a GList containing the children using gtk_container_get_children()
3. Get the first child using g_list_first() (this will be a GtkButton)
4. Connect to the button-press-event of that GtkButton. 
5. In your handler, if it's a right click do what you gotta do and return TRUE. Otherwise return FALSE to let the normal handlers run.

This is a bit tedious, however, you can use the same function to handle the "button-press-event" for every button and you could write a loop using gtk_toolbar_get_n_items() and gtk_toolbar_get_nth_item() rather than calling gtk_builder_get_object() on every GtkToolButton.

You may want to run this idea through the gtk-app-devel mailing list to get some feedback from those guys' as I've never had to do this. I would also put some checks to make sure that the child widget you get using gtk_container_get_child is in fact a GtkButton (GTK_IS_BUTTON()).

---

### Post by Vadi on 2008-06-09
Thanks, that worked!

---

### Post by SledgeHammer_999 on 2010-02-25
I think your first approach didn't work because containers don't have their own GdkWindow so they don't receive X events(if I remember correctly). Maybe this would work if you placed your container inside an eventbox and set the appropriate flags.

---

### Post by PmDematagoda on 2010-02-25
Regardless of how helpful your post maybe, posting it in an almost 2 year old thread is not that helpful and would most likely just create confusion.

Thread closed due to necromancy.

---

