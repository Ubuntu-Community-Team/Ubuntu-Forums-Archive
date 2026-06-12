---
title: "Glade + GladeGen + Python"
date: 2009-04-26
forum: Programming Talk
---

### Post by blazemore on 2009-04-26
I'm making an application with Glade, and I use GladeGen to generate the Python code for the window. I added a GTK button, and selected an icon for it from the /usr/share/icons folder.

However, when I run the .py file, the icon doesn't display.
Another problem is that the window is the smallest possible size (although I know this is something I need to do in Glade)

How can I
a) Get the icon to display properly?
b) Get the window to a fixed size?

---

### Post by blazemore on 2009-04-26
Okay never mind I found out I had to copy the icons to the project directory (oops... lol)

But now I have another question.
I don't know if it can be done, but how do you set a GTK button to focus on mouseover?

---

### Post by days_of_ruin on 2009-04-26
> **blazemore said:**
> Okay never mind I found out I had to copy the icons to the project directory (oops... lol)

But now I have another question.
I don't know if it can be done, but how do you set a GTK button to focus on mouseover?

Try connecting it to the "enter-notify-signal".
And in the callback do ```
button.get_focus()
```

---

### Post by blazemore on 2009-04-27
```
self.widgets['ButtonName'].get_focus()
```

gives me

```
AttributeError: 'gtk.Button' object has no attribute 'get_focus'
```

---

### Post by days_of_ruin on 2009-04-27
> **blazemore said:**
> ```
self.widgets['ButtonName'].get_focus()
```

gives me

```
AttributeError: 'gtk.Button' object has no attribute 'get_focus'
```

My bad. Use this instead:
```
button.set_flags(gtk.CAN_FOCUS)
buttons.**grab**_focus()
```

---

