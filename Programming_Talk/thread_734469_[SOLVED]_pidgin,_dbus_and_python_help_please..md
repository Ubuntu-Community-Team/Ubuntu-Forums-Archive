---
title: "[SOLVED] pidgin, dbus and python help please."
date: 2008-03-24
forum: Programming Talk
---

### Post by Glich on 2008-03-24
```
'''
hello, using pidgin instant messenger I can get the value of 'message' when one is being sent but, 
I dont know how to chage the value of message.

from the documentation (http://developer.pidgin.im/doxygen/dev/html/conversation-signals.html#sending-im-msg):
_____________________________
sending-im-msg:

Emitted before sending an IM to a user. message is a pointer to the message string, so the plugin can replace the message before being sent.
_____________________________

I think python get's a copy of the message (this is just a guess). How can I change the message before it is sent?

Thanks.
The code is taken from http://developer.pidgin.im/wiki/DbusHowto#Furtherreading and changed only a small amount.
'''

#!/usr/bin/env python

def cb_func(account, rec, message):
	#change message here somehow?    
	print message

import dbus, gobject
from dbus.mainloop.glib import DBusGMainLoop
dbus.mainloop.glib.DBusGMainLoop(set_as_default=True)
bus = dbus.SessionBus()

bus.add_signal_receiver(cb_func,
                        dbus_interface="im.pidgin.purple.PurpleInterface",
                        signal_name="SendingImMsg")

loop = gobject.MainLoop()
loop.run()
```

---

### Post by Roptaty on 2008-03-25
Using dbus you can only get information from Pidgin, you cant modify the information. To do this, you need to write a plugin loaded in Pidgin. (See [http://developer.pidgin.im/wiki/DbusHowto](http://developer.pidgin.im/wiki/DbusHowto) )

---

### Post by Glich on 2008-03-25
Yes, I need to read that better. Thanks for pointing it out. I'm thinking of making a plugin that will allow python to have more control.

---

