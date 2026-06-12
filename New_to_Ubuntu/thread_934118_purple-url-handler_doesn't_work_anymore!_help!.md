---
title: "purple-url-handler doesn't work anymore! help!"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Sarah L on 2008-09-30
Hi guys,
I've recently downgraded from Firefox 3 to Firefox 2 and I have to say, the older browser works like a charm. Features that I had to hack and tweak to get working in FF3 already work out of the box in FF2. One of them is support for the aim: protocol - FF2 already knows how to pass calls to purple-url-handler, which opens up a new conversation in Pidgin.

This worked fine the first few times I tried it. Then, for some unknown reason, it suddenly stopped working for me today. All calls to purple-url-handler, whether through Firefox or via the terminal, give me this output:

```

Traceback (most recent call last):
  File "/usr/bin/purple-url-handler", line 9, in <module>
    obj = dbus.SessionBus().get_object("im.pidgin.purple.PurpleService", "/im/pidgin/purple/PurpleObject")
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name im.pidgin.purple.PurpleService was not provided by any .service files

```

I haven't installed any additional addons or changed any Firefox settings (manually, at least). What might have caused this sudden :(?

---

### Post by aeiah on 2008-09-30
is dbus running right?
```

ps ux|grep dbus-daemon
```

---

### Post by Sarah L on 2008-09-30
Dbus appears to be running.

```

30320  0.0  0.0   2564   912 ?        Ss   08:16   0:00 /usr/bin/dbus-daemon --fork --print-pid 7 --print-address 9 --session
32621  0.0  0.0   3008   768 pts/1    S+   08:46   0:00 grep dbus-daemon

```

---

### Post by Sarah L on 2008-10-06
bump

---

