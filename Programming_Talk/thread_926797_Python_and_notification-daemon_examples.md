---
title: "Python and notification-daemon examples?"
date: 2008-09-22
forum: Programming Talk
---

### Post by forger on 2008-09-22
Hi, I probably need to read a lot about notification-daemon and dbus, but I searched in google and couldn't find an example to show how to send a notification popup using python through the notification-daemon. Can someone share an example here?

Also, the python application I'm helping to code will be run as root, what is the best way to send a popup notification through notification-daemon but for another user that is logged in and uses a desktop manager, say gnome? An example here would also be welcome :)

---

### Post by forger on 2008-09-22
Ok, so I found pynotify
```
#!/usr/bin/env python
try:
    import gtk, pygtk, os, os.path, pynotify
    pygtk.require('2.0')
except:
    print "Error: need python-notify, python-gtk2 and gtk"

if __name__ == '__main__':
    if not pynotify.init("Timekpr notification"):
        sys.exit(1)

    n = pynotify.Notification("Moo title", "test")
    #n = pynotify.Notification("Moo title", "test", "file:///path/to/icon.png")
    n.set_urgency(pynotify.URGENCY_CRITICAL)
    n.set_timeout(10000) # 10 seconds
    n.set_category("device")

    #Call an icon
    helper = gtk.Button()
    icon = helper.render_icon(gtk.STOCK_DIALOG_WARNING, gtk.ICON_SIZE_DIALOG)
    n.set_icon_from_pixbuf(icon)

    if not n.show():
        print "Failed to send notification"
        sys.exit(1)
```

What's the best way to send this to a specific user while running in as root in background? :confused:

---

### Post by evrkusd on 2009-05-09
did you ever find a way to do this or examples of this working?

---

### Post by unutbu on 2009-05-09
To run a notifier script as root, but have the notification show up on a user's display, see [http://gnome-hacks.org/hacks.html?id=82](http://gnome-hacks.org/hacks.html?id=82).

I've found to get this script to work on Ubuntu, I needed to change

```

pids=`pgrep -u $user gnome-session`

```

to

```

pids=$(pgrep -u $user gnome-panel)

```

---

### Post by days_of_ruin on 2009-05-09
Here are some more examples. [https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Layout%20cases%20(with%20examples%20in%20C,%20Python%20and%20C#)]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#Layout%20cases%20(with%20examples%20in%20C,%20Python%20and%20C#)")

[SIZE="1"]Btw I would put your main code in a function called main and
then below "if __name__ == "__main__":"
just put main().[/SIZE]

---

### Post by NoBugs! on 2010-03-06
There seems to be a bug in this notification system,
no matter what timeout you set in n.set_timeout(number), it always shows the notification for 11 seconds.

---

### Post by kostkon on 2010-03-06
> **NoBugs! said:**
> There seems to be a bug in this notification system,
no matter what timeout you set in n.set_timeout(number), it always shows the notification for 11 seconds.
Actually, it isn't a bug, it's a feature. Quoting  [from the wiki page]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines")
> Notify OSD does not use the expire_timeout parameter.

---

