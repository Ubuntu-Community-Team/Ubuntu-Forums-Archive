---
title: "Python dbus"
date: 2009-03-13
forum: Programming Talk
---

### Post by matmatmat on 2009-03-13
Does anyone know how to use dbus in python? I'm trying to do this:
[PHP]
dbus-send --type=method_call --dest=org.kde.amarok /Player org.freedesktop.MediaPlayer.Pause
[/PHP]
only in python.
Thanks in advanced.

---

### Post by imdano on 2009-03-13
It'll look something like this[php]import dbus
bus = dbus.SessionBus()
proxy_obj = bus.get_object("org.kde.amarok", "/org/freedesktop/MediaPlayer")
player = dbus.Interface(proxy_obj, "org.freedesktop.MediaPlayer")
player.Pause()[/php]This is untested, and there's a decent chance I mixed up object name vs well-known name or something like that, so it may give you an error.

See the python-dbus tutorial: [http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html](http://dbus.freedesktop.org/doc/dbus-python/doc/tutorial.html)

---

### Post by matmatmat on 2009-03-14
Thanks for the reply, I ran it & it gave this error:
```

dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownObject: No such object path '/org/freedesktop/MediaPlayer'

```
?

---

### Post by imdano on 2009-03-14
Like I said, it's untested.  Try using /Player instead.

---

### Post by eightmillion on 2009-03-14
This code will work:

[php]
import dbus
bus = dbus.SessionBus()
player = bus.get_object("org.kde.amarok", "/Player")
player.Pause() 

[/php]

---

### Post by matmatmat on 2009-03-15
Thanks, it worked!

---

