---
title: "How to associate Notification with Tray Icon? (in Python)"
date: 2008-06-07
forum: Programming Talk
---

### Post by ::: on 2008-06-07
I want to associate a Notification with a Tray Icon. So that the Notification appears near the Tray Area and points to the associated Tray Icon. For example, the Ubuntu Update Notification does this:
[IMG]http://www.ubuntu.com/files/u3/update-notification.png[/IMG]


I know how to create a Tray Icon (gtk.StatusIcon) and how to create a Notification (pynotify.Notification). However, I don't know how make the Notification point to the StatusIcon. Can anyone help?

---

### Post by fred.reichbier on 2008-06-07
Hello,

I used the same in gestikk and that's my code:

```
class Notifier:
    """ class for notifying the user when a gesture started """
    def __init__(self, logic, statusicon):
        self.logic = logic
        self.statusicon = statusicon

    def notify(self, s, gesture):
        """ Notify and display `s`
            :type s: String
        """
        notify = pynotify.Notification(_("Notification"), s.replace('<', '').replace('>', '-')) # TODO: it doesn't display < and >? o.O
        screen, rect, orient = self.statusicon.icon.get_geometry()
[COLOR="DarkOrange"]        notify.set_hint("x", rect.x + (rect.width / 2))
        notify.set_hint("y", rect.y + (rect.height / 2))[/COLOR]
        notify.set_timeout(3000) # timeout in ms
        color = self.logic.config_get_option('OSD', 'color', '#0000FF')
        pb = pixmap_to_pixbuf(gesture_to_pixmap(gesture2py(gesture), 40, color), (255, 255, 255))
        notify.set_icon_from_pixbuf(pb)
        notify.show()
```

self.statusicon is the gtk.StatusIcon. I highlighted the interesting lines for you ;)

Fred

---

### Post by loell on 2008-06-07
I believe there's a method in pynotify to attach the notification widget on to a gtk widget as the native C api has it.

ah, you can use the method **attach_to_status_icon**

---

### Post by blaz_boy on 2008-08-04
thanx loell so much , i was searching for that 
and fred.reichbier : 
i'v tried ur code and it didn't work plz check it for me :) thanks

---

### Post by blaz_boy on 2008-08-04
thanx loell so much , i was searching for that 
and fred.reichbier : 
i'v tried ur code and it didn't work plz check it for me :) thanks

---

