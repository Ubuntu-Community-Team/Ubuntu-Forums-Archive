---
title: "[Python/PyGtk] Want to  make a chat window..."
date: 2011-06-21
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
hey folks... i want to make a chat window in pygtk....what should i use to make such a window...i mean should i use a vbox with a scroll bar and entry() to append text entered by user or is thre anything that makes this easier?????

---

### Post by StephenF on 2011-06-21
gtk.TextView to show the replies. gtk.ScrolledWindow also.

Have you thought about the chat back-end. Some kind of instant messaging protocol or IRC?

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
> **StephenF said:**
> gtk.TextView to show the replies. gtk.ScrolledWindow also.

Have you thought about the chat back-end. Some kind of instant messaging protocol or IRC?
But isn't textview supposed to show u contents of a file....i am asking this because i am working on a LAN messenger..

---

### Post by simeon87 on 2011-06-21
> **Dhiraj Thakur(Invincible) said:**
> But isn't textview supposed to show u contents of a file....i am asking this because i am working on a LAN messenger..

TextView is for displaying text. It does not matter where the text comes from. It could be from a file but you can also place your own text there, such as chat messages.

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
> **simeon87 said:**
> TextView is for displaying text. It does not matter where the text comes from. It could be from a file but you can also place your own text there, such as chat messages.
okay thanks....so can we combine it with a entry box to make a chat box....?? :)

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-21
Thanks for the help folks....i hav created the app myself here's the code

```

[B]import pygtk,gtk


def butt_call(widget,data=None):
    iter = buffer1.get_iter_at_offset(-1)
    buffer1.insert(iter,("\n Username: "+entry.get_text()))
    entry.set_text("")

win=gtk.Window()
win.connect("destroy",lambda wid:gtk.main_quit())
vbox=gtk.VBox()
win.add(vbox)
view=gtk.TextView()
view.set_editable(False)
buffer1=view.get_buffer()
scrolled_window=gtk.ScrolledWindow()
scrolled_window.set_policy(gtk.POLICY_AUTOMATIC,gtk.POLICY_AUTOMATIC)
scrolled_window.add(view)
vbox.add(scrolled_window)
entry=gtk.Entry()
button=gtk.Button("Enter")
button.connect("clicked",butt_call)
hbox=gtk.HBox()
hbox.add(entry)
hbox.add(button)
vbox.add(hbox)
win.show_all()
gtk.main()

[/B]
```

---

