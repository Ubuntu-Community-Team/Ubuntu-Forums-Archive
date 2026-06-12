---
title: "GtkEntry &quot;activate&quot; signal"
date: 2010-03-11
forum: Programming Talk
---

### Post by Milliways on 2010-03-11
The GTK+ 2.0 Tutorial states:-
If we want to catch when the user has entered text, we can connect to the activate or changed signal.
Activate is raised when the user hits the enter key within the Entry widget.

and then gives an example.

However the GTK+ Reference Manual states:-

The "activate" signal
void user_function (GtkEntry *entry, gpointer  user_data)
A keybinding signal which gets emitted when the user activates the entry.
**Applications should not connect to it**, but may emit it with g_signal_emit_by_name() if they need to control activation programmatically.

Why should "Applications should not connect to it"?

---

