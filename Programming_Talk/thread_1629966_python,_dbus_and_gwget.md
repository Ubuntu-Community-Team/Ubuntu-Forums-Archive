---
title: "python, dbus and gwget"
date: 2010-11-24
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-11-24
Hello there,

I am trying to fix a python script designed for Skype (so that the launcher does not start a new instance each time), which i would like to adapt for Gwget.

The script is:
[PHP]#!/usr/bin/env python
import dbus
import sys
import os

try:
    # Try and set skype window to normal
    remote_bus = dbus.SessionBus()
    out_connection = remote_bus.get_object('com.Skype.API', '/com/Skype')
    out_connection.Invoke('NAME mySkypeController')
    out_connection.Invoke('PROTOCOL 5')
    #out_connection.Invoke('SET WINDOWSTATE MAXIMIZED')
    out_connection.Invoke('SET WINDOWSTATE NORMAL')
    out_connection.Invoke('FOCUS')
except:
    os.system("skype")
    sys.exit()[/PHP]

So i am very new to Dbus, i read quickly through the documentation, but i still find it quite obscure. I especially don't understand how i am supposed to find out what the objects, addresses, methods and signals are for Gwget. The only thing i found was the org.gnome.gwget.service in the /usr/share/dbus-1/services path.

I must be honest, although i am interested, i just need the script and have little time at the moment to spend learning more python. So if you could help me getting through this quickly, i would really appreciate it.

Thanks.
Benjamin

---

