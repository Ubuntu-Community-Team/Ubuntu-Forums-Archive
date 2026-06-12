---
title: "Ubuntu Notifictions"
date: 2011-06-19
forum: Programming Talk
---

### Post by Dhiraj Thakur(Invincible) on 2011-06-19
Hey guys i really like the notifications in ubuntu which appear in top right hand corner of ur screen and then fade away after sometime ..... i wanted to know how r they produced .... can i produce such notifications in python using libraries like Pygtk etc... ??             :confused:

---

### Post by r-senior on 2011-06-19
You need pynotify ... very simple to do.

```

import pynotify

...

    title = ???
    message = ???
    icon = ???

    notification = pynotify.Notification(title, message, icon)
    notification.show()


```

---

### Post by Dhiraj Thakur(Invincible) on 2011-06-19
thanks very much r-senior how did u know that??  just curious ;)

and one thing these notifications do not work in windows in fact windows has no module named pynotify...
so how to produce such notifictions in windows (:mad:)  ???:confused:

---

### Post by r-senior on 2011-06-19
I think I probably read it in this forum. ;)

Given that pynotify is a wrapper around [GNOME libnotify]("http://developer.gnome.org/libnotify/"), it does make your program GNOME-specific.

---

