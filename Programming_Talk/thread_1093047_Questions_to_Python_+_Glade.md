---
title: "Questions to Python + Glade"
date: 2009-03-11
forum: Programming Talk
---

### Post by inoitna on 2009-03-11
hi everyone,

I just started learning python and glade tutorial recently.

I would like to create an application to link up windows, 

When i open the <<project4.py>>..ya, it's fine...and i click ok link to 2nd window also no problem...

My problem here is when i close the second window and click ok again, the content inside the second window was gone. I can't get any solution from google.

Please helps...Thanks...

Here is my project:

---

### Post by days_of_ruin on 2009-03-11
```
window.connect("delete_event",func)
 
#func
def func(widget,data=None):
    return widget.hide_on_delete()

```

---

### Post by inoitna on 2009-03-11
> **days_of_ruin said:**
> ```
window.connect("delete_event",func)
 
#func
def func(widget,data=None):
    return widget.hide_on_delete()

```

hey bro...

the problem isn't solve yet...

Something wrong with my code?


thanks

---

### Post by Can+~ on 2009-03-11
> **inoitna said:**
> hey bro...

hey dawg, I herd u leik pythons. (couldn't resist)

As for your problem goes, you just messed up with the destroy event. When you hit the "X" button of window2, the function [FONT="Courier New"]hide_window2[/FONT] is not being called. After checking the .glade file, I realized why; the field was empty, here's how it should look like:

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-1.png[/IMG]

Simple mistake.

(Notice that you must add signal names on the .glade file, and then use the same name on the python script for the autoconnect to do it's magic, I write this, because there actually no signals set in your .glade file)

---

### Post by inoitna on 2009-03-12
> **Can+~ said:**
> hey dawg, I herd u leik pythons. (couldn't resist)

As for your problem goes, you just messed up with the destroy event. When you hit the "X" button of window2, the function [FONT="Courier New"]hide_window2[/FONT] is not being called. After checking the .glade file, I realized why; the field was empty, here's how it should look like:

[IMG]http://img.photobucket.com/albums/v517/CanXp/screenshot1-1.png[/IMG]

Simple mistake.

(Notice that you must add signal names on the .glade file, and then use the same name on the python script for the autoconnect to do it's magic, I write this, because there actually no signals set in your .glade file)

My dawg, it's work...
couldn't believe it is just so simple

Thanks much...

---

### Post by inoitna on 2009-03-12
hi Can+,

Im thinking to create a blutooth pentester GUI, so is it possible for me to call the bluetooth pentester command when the <<OK>> button is clicked?

---

