---
title: "Python display gnome's black alert panels"
date: 2011-05-22
forum: Programming Talk
---

### Post by MegaLoler on 2011-05-22
I am writing a program in Python that I want to know how to display messages on gnome's black alert boxes that appear in the corner of the screen.  I don't know what they are called.  An example would be when RhythmBox displays notifications for each song that comes on.  Can anyone tell me how to do this with Python?  Thanks

EDIT: I found out what they are called.  They are called notifications.  You can use them with python with the pynotify module.

```
import pynotify

notification = pynotify.Notification("Title", "Description")
notification.show()
```

---

