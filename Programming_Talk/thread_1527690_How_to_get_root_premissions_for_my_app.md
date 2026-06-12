---
title: "How to get root premissions for my app?"
date: 2010-07-09
forum: Programming Talk
---

### Post by zimio on 2010-07-09
My app needs to do some privileged work. I've been looking everywhere, but I can't find anything useful. I know I want to use Policykit1 and dbus because all the other alternatives I've found aren't used anymore. 

This is the code I got so far:

```

import dbus
import os

bus = dbus.SystemBus()
proxy = bus.get_object('org.freedesktop.PolicyKit1', '/org/freedesktop/PolicyKit1/Authority')
authority = dbus.Interface(proxy, dbus_interface='org.freedesktop.PolicyKit1.Authority')

system_bus_name = bus.get_unique_name()

subject = ('system-bus-name', {'name' : system_bus_name})
action_id = 'org.freedesktop.policykit.exec'
details = {}
flags = 1            # AllowUserInteraction flag
cancellation_id = '' # No cancellation i


result = authority.CheckAuthorization(subject, action_id, details, flags, cancellation_id)

os.makedirs('/usr/local/share/somefolder')

```

I can't make the directory, what am I doing wrong?

---

