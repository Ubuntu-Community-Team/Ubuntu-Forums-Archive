---
title: "Bluetooth system based on Python"
date: 2010-02-22
forum: Programming Talk
---

### Post by smoove52 on 2010-02-22
Hi. I'm searching for programmers help. Now I'm developing data transmission system based on Bluetooth technology, Python language and I need to get an Bluetooth RSSI value from mobile devices. I downloaded this script:

[http://technical.net-fb.de/python_bluetooth.html](http://technical.net-fb.de/python_bluetooth.html)

and the problem occurs. I'm working with Nokia N95 8GB, Nokia E65 mobile devices and ASUS P535 pocket pc. But when I'm trying to measure RSSI value I simple got 0 values. No errors or smth, but this value I think isn't correct, because its same everytime. Maybe somebody could help me to cope with this?

Also when I'm trying to use this script:

[http://wiki.bluez.org/wiki/HOWTO/DiscoveringDevices](http://wiki.bluez.org/wiki/HOWTO/DiscoveringDevices)

I got an error: 
File "./Signal.py", line 30, in <module>
    adapter.DiscoverDevices()
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "DiscoverDevices" with signature "" on interface "org.bluez.Adapter" doesn't exist

Thanks for help in advance.

---

