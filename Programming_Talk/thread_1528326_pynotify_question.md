---
title: "pynotify question"
date: 2010-07-10
forum: Programming Talk
---

### Post by NikitaUtiu on 2010-07-10
I have been recently working on a project using pynotify. I want to know if there is any way to set the time the notification is visible ?

n = pynotify.Notification ("blah blah", "blah blah")
# for example

And any member function or something to set the amount of time the notification on befor it closes?
P.S. Using Ubuntu (GNOME)

---

### Post by detrate on 2010-07-11
After initializing your notification object (like you did), use:

```
n.set_timeout(10000)
```

time is in milliseconds.

You may also be interested in experimenting with the following:

Set urgency:
```
n.set_urgency(pynotify.URGENCY_LOW)
n.set_urgency(pynotify.URGENCY_NORMAL)
n.set_urgency(pynotify.URGENCY_CRITICAL)

```

Set icon:
```
icon = helper.render_icon(gtk.STOCK_DIALOG_QUESTION, gtk.ICON_SIZE_DIALOG)
n.set_icon_from_pixbuf(icon)
```


The pynotify api documentation is close to non-existent.  I ran through similar problems a few weeks ago.  Good Luck :)

---

