---
title: "Trouble with GTK &amp; C"
date: 2008-09-08
forum: Programming Talk
---

### Post by Amon_Re on 2008-09-08
Hey guys,

I've spent the better half of an evening trying to figure out how to do the following:

In my C application, i have a function called "delete_event" that gets hooked to the "delete-event" of a GTK window.

Trying to close the window triggers this function, gives a nice pop-up with a warning, everything seems to be working fine, however, i now added a menu to this window, and i want to trigger the same function when "file->quit" is called.

Frankly, i'm stuck, I can add a nice callback function to the menu-item, and it gets called & all, but i have no idea how to go from an "activated" menu-item to a "delete-event" on a window.

I thought about sending a signal to the window with a delete-event in there, but i can't seem to figure out how to use g_signal_emit(), nor what the id is for the "delete-event".

I expected this to be an obvious thing, but eighter i'm too tired right now, or it's not :lolflag:

---

### Post by kknd on 2008-09-08
Instead of emitting another signal, can't you just connect to the same callback as delete-event?

---

### Post by Amon_Re on 2008-09-09
> **kknd said:**
> Instead of emitting another signal, can't you just connect to the same callback as delete-event?

Unfortuneatly, no because a menu selection is an "Activate" event, thus it doesn't migrate towards a "Destroy". (delete_event returns FALSE when quiting and therefor it goes down the chain to a "Destroy" event.)

---

### Post by nvteighen on 2008-09-09
Looking at GTK+'s docs (btw, have you installed them (libgtk2.0-doc package) and the Devhelp "documentation browser" (devhelp)), maybe what you need is g_signal_emit_by_name() to send a "delete-event" signal to the window.

---

### Post by SledgeHammer_999 on 2008-09-09
The signal handler of the menu item should just destroy/close/terminate the window. And when the window is destroyed/closed/terminated the "delete-event" handler will be called.

---

### Post by Amon_Re on 2008-09-09
> **nvteighen said:**
> Looking at GTK+'s docs (btw, have you installed them (libgtk2.0-doc package) and the Devhelp "documentation browser" (devhelp)), maybe what you need is g_signal_emit_by_name() to send a "delete-event" signal to the window.

Hi nvteighen,

No, i didn't have devhelp installed, i've been using the online reference, thx for that one, never heard of devhelp before :)

I tried implementing my goal using g_signal_emit_by_name(), but i keep getting this error:

```
GLib-GObject-CRITICAL **: g_signal_emit_by_name: assertion `detailed_signal != NULL' failed
```

This is my call:
```
g_signal_emit_by_name(G_OBJECT (data), GDK_DELETE);
```

Where data is a pointer to my Window's GtkWidget.

---

### Post by Amon_Re on 2008-09-09
> **SledgeHammer_999 said:**
> The signal handler of the menu item should just destroy/close/terminate the window. And when the window is destroyed/closed/terminated the "delete-event" handler will be called.

How? Menu-selections get triggered by "Activate" signals, not "delete" nor "destroy" signals, so just putting in a callback to my current delete_event() function won't do it (since this just returns FALSE when the user wants to exit, whereby the following event is a "destroy" event).

This would go much better had i had a clue about gtk :P

---

### Post by Amon_Re on 2008-09-09
Scratch this, i'm going back to the drawingboard, i'll make my exit function more flexible.

Thx for all your help tho guys ;)

---

### Post by SledgeHammer_999 on 2008-09-09
> **Amon_Re said:**
> How? Menu-selections get triggered by "Activate" signals, not "delete" nor "destroy" signals, so just putting in a callback to my current delete_event() function won't do it (since this just returns FALSE when the user wants to exit, whereby the following event is a "destroy" event).

This would go much better had i had a clue about gtk :P

No. What I meant is this. You have 2 signal handlers. 1 handles the "destroy" event and the other handles the "activate" event. When you click the menu item your "activate" handler is called. Inside your "activate" handler you issue the command to destroy the window. When you issue that command a "destroy" event is emmited. This "destroy" event is then handled by the "destroy" handler!

---

### Post by nvteighen on 2008-09-10
[> **Amon_Re said:**
> 
I tried implementing my goal using g_signal_emit_by_name(), but i keep getting this error:

```
GLib-GObject-CRITICAL **: g_signal_emit_by_name: assertion `detailed_signal != NULL' failed
```

This is my call:
```
g_signal_emit_by_name(G_OBJECT (data), GDK_DELETE);
```


What does GDK_DELETE define? The name should be "delete_event"... unless you have arranged a macro by your own (but if GDK_DELETE is a macro of yours, use a different name... MY_DELETE)

> **SledgeHammer_999 said:**
> No. What I meant is this. You have 2 signal handlers. 1 handles the "destroy" event and the other handles the "activate" event. When you click the menu item your "activate" handler is called. Inside your "activate" handler you issue the command to destroy the window. When you issue that command a "destroy" event is emmited. This "destroy" event is then handled by the "destroy" handler!

Do you mean something like this?
```

g_signal_connect(G_OBJECT(MyWin), "destroy_event", G_CALLBACK(exit_function), NULL);
g_signal_connect(G_OBJECT(MenuObj), "activate", G_CALLBACK(gtk_widget_destroy), MyWin);

```

(btw, here we're lucky we just need to pass one argument into gtk_widget_destroy()... otherwise either you create a wrapper that takes an array of gpointers, splits them and pass the arguments to the real function... or maybe you'd have to use GClosures)

---

### Post by SledgeHammer_999 on 2008-09-10
> **nvteighen said:**
> Do you mean something like this?
```

g_signal_connect(G_OBJECT(MyWin), "destroy_event", G_CALLBACK(exit_function), NULL);
g_signal_connect(G_OBJECT(MenuObj), "activate", G_CALLBACK(gtk_widget_destroy), MyWin);

```

(btw, here we're lucky we just need to pass one argument into gtk_widget_destroy()... otherwise either you create a wrapper that takes an array of gpointers, splits them and pass the arguments to the real function... or maybe you'd have to use GClosures)

I haven't used GTK directly I have used gtkmm(C++) so I am writing pseudo-code here:
[php]
g_signal_connect(G_OBJECT(MyWin), "destroy_event", G_CALLBACK(exit_function), NULL);
g_signal_connect(G_OBJECT(MenuObj), "activate", G_CALLBACK(menu_quit_function), NULL);

void exit_function()
{
 //do your cleaning up before the window is destroyed
}

void menu_quit_function()
{
  gtk_widget_destroy(&window); 
//'window' is a a GtkWindow. after this command a "destroy" event is emmited and the 'exit_function()' handler is called(automatically).
}[/php]

I hope you understood what I mean :D

---

### Post by nvteighen on 2008-09-10
I tested my proposal and it doesn't work... actually, it will destroy your menu or button or whatever you pressed... :p

> **SledgeHammer_999 said:**
> I haven't used GTK directly I have used gtkmm(C++) so I am writing pseudo-code here:
[php]
g_signal_connect(G_OBJECT(MyWin), "destroy_event", G_CALLBACK(exit_function), NULL);
g_signal_connect(G_OBJECT(MenuObj), "activate", G_CALLBACK(menu_quit_function), NULL);

void exit_function()
{
 //do your cleaning up before the window is destroyed
}

void menu_quit_function()
{
  gtk_widget_destroy(&window); 
//'window' is a a GtkWindow. after this command a "destroy" event is emmited and the 'exit_function()' handler is called(automatically).
}[/php]


The same rewritten in proper C (your pseudocode was a bit C++-ish?):
[php]
g_signal_connect(G_OBJECT(MyWin), "destroy_event", G_CALLBACK(exit_function), NULL);
g_signal_connect(G_OBJECT(MenuObj), "activate", G_CALLBACK(menu_quit_function), MyWin);

void exit_function(void)
{
 /* do your cleaning up before the window is destroyed */
}

void menu_quit_function(gpointer window)
{
  gtk_widget_destroy(window);
}[/php]

Nice to work with you! (Now, where's the OP?)

---

### Post by Amon_Re on 2008-09-10
Well, i worked arround the problem by writing a function called "_Exit", that gets called when the window receives a delete_event, or when i select the menu-item.

Instead of relying on the chaining of events (delete > destroy) i do it all in _Exit, and it works with less code, being semi-awake tends to improve coding compared to mostly-asleep :)

---

### Post by SledgeHammer_999 on 2008-09-10
> **nvteighen said:**
> I tested my proposal and it doesn't work... actually, it will destroy your menu or button or whatever you pressed... :p



The same rewritten in proper C (your pseudocode was a bit C++-ish?):
[php]
g_signal_connect(G_OBJECT(MyWin), "destroy_event", G_CALLBACK(exit_function), NULL);
g_signal_connect(G_OBJECT(MenuObj), "activate", G_CALLBACK(menu_quit_function), MyWin);

void exit_function(void)
{
 /* do your cleaning up before the window is destroyed */
}

void menu_quit_function(gpointer window)
{
  gtk_widget_destroy(window);
}[/php]

Nice to work with you! (Now, where's the OP?)

Yup you are right. I assumed that my "functions" were in the same class(this class implements the window). Now, I remembered that C has no classes and you need to pass a pointer to your window :D

---

