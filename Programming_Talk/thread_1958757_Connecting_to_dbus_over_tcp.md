---
title: "Connecting to dbus over tcp"
date: 2012-04-14
forum: Programming Talk
---

### Post by silverair on 2012-04-14
I wrote a simple python program to play and pause banshee music player.
While its working on my own machine, I have trouble doing it to a remote computer, connected to the same router (LAN).
I edited the session.conf of the remote machine, to add this line:
```
<listen>tcp:host=localhost,port=12434</listen>
```

and here is my program:
```
import dbus


bus_obj=dbus.bus.BusConnection("tcp:host=localhost,port=12434")

proxy_object=bus_obj.get_object('org.bansheeproject.Banshee',
                       '/org/bansheeproject/Banshee/PlayerEngine')

playerengine_iface=dbus.Interface(proxy_object,
		dbus_interface='org.bansheeproject.Banshee.PlayerEngine')
                       
var=raw_input("\nPress\n1 to play\n2 to pause\n3 to exit\n")

while (var!="3"):
	var=raw_input("\nPress\n1 to play\n2 to pause\n3 to exit\n")


	if var=="1":
		print "playing..."
		playerengine_iface.Play()
	
	elif var=="2":
		print "pausing"
		playerengine_iface.Pause()



```

This is what i get when i try to execute it
Traceback (most recent call last):
  File "dbus3.py", line 4, in <module>
    bus_obj=dbus.bus.BusConnection("tcp:host=localhost,port=12434")
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket "localhost:12434" Connection refused

What am I doing wrong here?
should i edit /usr/lib/python2.7/dist-packages/dbus/bus.py

---

### Post by silverair on 2012-04-15
ok, here is the deal 
when i add 
<listen>tcp:host=192.168.1.7,port=12434</listen>
to to /etc/dbus-1/session.conf, then reboot, hoping it would start listening on reboot,
It never boots. It gets stuck on loading screen and occasionally, a black screen with the following text flashes:

Pulseaudio Configured For Per-user Sessions Saned Disabled;edit/etc/default/saned
so, when i go ctrl+alt+f1 , change session.conf to original state and reboot, it boots properly.

Whats all that about?
How can I make dbus daemon listen for tcp connections, without encountering problems?

---

