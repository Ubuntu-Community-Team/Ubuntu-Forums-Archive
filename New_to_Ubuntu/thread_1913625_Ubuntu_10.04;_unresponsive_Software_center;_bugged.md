---
title: "Ubuntu 10.04; unresponsive Software center; bugged python"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by Kabroon on 2012-01-22
I'm trying to add software sources to get wine for ubuntu lucid.
I tried doing it the terminal way as my software manager is buggy anyway,
doesn't reply when I click install, or remove for exampple, but I got lost,
so I resorted to the ui. However, no success there and python seems to be the problem.

Upon opening Software center from terminal I get this

```

Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 579, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 75, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/transactionswatcher.py", line 39, in _register_active_transactions_watch
    apt_daemon = aptdaemon.client.get_aptdaemon()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 897, in get_aptdaemon
    False),
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 579, in msg_reply_handler
    *message.get_args_list()))
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 75, in error_cb
    callback('')
  File "/usr/share/software-center/softwarecenter/backend/transactionswatcher.py", line 39, in _register_active_transactions_watch
    apt_daemon = aptdaemon.client.get_aptdaemon()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 897, in get_aptdaemon
    False),
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()

```

Edit -> Software sources
(no response)

```

Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/app.py", line 375, in _poll_software_sources_subprocess
    self.run_update_cache()
  File "/usr/share/software-center/softwarecenter/app.py", line 432, in run_update_cache
    self.backend.reload()
  File "/usr/share/software-center/softwarecenter/backend/aptd.py", line 116, in reload
    error_handler=self._on_trans_error)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 781, in update_cache
    error_handler)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 851, in _run_transaction
    self.apt_control = get_aptdaemon()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/client.py", line 897, in get_aptdaemon
    False),
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 244, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 241, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 183, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 281, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Launch helper exited with unknown return code 1
```

---

