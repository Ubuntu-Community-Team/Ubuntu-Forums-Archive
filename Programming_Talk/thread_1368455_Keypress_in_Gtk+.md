---
title: "Keypress in Gtk+"
date: 2009-12-30
forum: Programming Talk
---

### Post by Milliways on 2009-12-30
I have captured keyboard events so I can respond to these with the following c code:-
g_signal_connect(G_OBJECT(window), "key_press_event", G_CALLBACK(key_press_cb), &tree);

Unfortunately this stops other widgets e.g scrolledwindow respondng to keys.

How do I capture keys, but allow those I do not need to pass through to gtk+

---

### Post by SledgeHammer_999 on 2009-12-30
From the [docs](http://library.gnome.org/devel/gtk/stable/GtkWidget.html#GtkWidget-key-press-event):

> 
The ::key-press-event signal is emitted when a key is pressed.

To receive this signal, the GdkWindow associated to the widget needs to enable the GDK_KEY_PRESS_MASK mask.

This signal will be sent to the grab widget if there is one.

widget :
	the object which received the signal

event :
	the GdkEventKey which triggered this signal

user_data :
	user data set when the signal handler was connected.

[b]Returns :
	TRUE to stop other handlers from being invoked for the event. FALSE to propagate the event further.[/b]


(focus on the bold)

---

