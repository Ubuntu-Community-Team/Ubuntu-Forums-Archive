---
title: "sudo system-config-printer"
date: 2014-06-11
forum: New to Ubuntu
---

### Post by dee7 on 2014-06-11
Xubuntu 14.04 ERROR:root:Could not find any typelib for GnomeKeyring ?? I've ignored this but should I ?

---

### Post by Toz on 2014-06-15
When/where are you getting this error message? What are you trying to do that generates the error?

---

### Post by UnixMan2 on 2014-06-23
Same(?) problem here. Ubuntu 14.04 server, fresh install. I've added system-config-printer (with deps) via apt. But this is all I get if I try to run it:

```

# system-config-printer
/usr/lib/python2.7/dist-packages/gi/overrides/Gtk.py:50: RuntimeWarning: You have imported the Gtk 2.0 module.  Because Gtk 2.0 was not designed for use with introspection some of the interfaces and API will fail.  As such this is not supported by the pygobject development team and we encourage you to port your app to Gtk 3 or greater. PyGTK is the recomended python module to use with Gtk 2.0
  warnings.warn(warn_msg, RuntimeWarning)
ERROR:root:Could not find any typelib for GnomeKeyring
Traceback (most recent call last):
  File "/usr/share/system-config-printer/newprinter.py", line 2629, in on_expNPDeviceURIs_expanded
    padding, pack_type) = parent.query_child_packing (widget)
TypeError: query_child_packing() takes exactly 6 arguments (2 given)
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 2132, in <module>
    main(show_jobs)
  File "/usr/share/system-config-printer/system-config-printer.py", line 2106, in main
    mainwindow = GUI()
  File "/usr/share/system-config-printer/system-config-printer.py", line 428, in __init__
    [Gtk.TargetEntry.new("queue", 0, 0)],
AttributeError: type object 'TargetEntry' has no attribute 'new'

```

---

### Post by pqwoerituytrueiwoq on 2014-06-23
Why are you running it as root?
that application uses a GUI, i notice you are running a server so unless you installed one you don't have that
run ```
lynx 127.0.0.1:631
``` to configure your printer without a GUI

---

