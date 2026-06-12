---
title: "python - dbus as IPC for web service problem"
date: 2009-03-19
forum: Programming Talk
---

### Post by kannerke on 2009-03-19
Hello all,

I'm trying to use dbus inside cgi-python scripts as IPC to communicate with external processes running on the web server.

The first error I encountered was:
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ExecFailed: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed

I was able to solve this by putting the environment variables, returned by executing the dbus-launch command, see
[http://stackoverflow.com/questions/257658?sort=votes](http://stackoverflow.com/questions/257658?sort=votes)


At this point, I encounter the following problem:
DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name path.to.my.service was not provided by any .service files

My target service was running and waiting for incoming dbus calls.

This problem was not totally unexpected because executing the 'dbus-launch' command probably initiates a new dbus.


Can someone help me with how to connect to the right dbus calling bus = dbus.SessionBus() or how to connect the new dbus with the exisitng dbus.


To be clear: I have a python script running in a terminal, registered a dbus service and a python cgi script, executed by apache2 willing to access this service.


kind regards,
Peter

---

### Post by kannerke on 2009-03-25
Hello all,

I managed to get it working :-). I needed to changed two things:

- first, I had to change the bus I used: I used the SessionBus instead of the SystemBus. Using the SystemBus, services are available through the whole system.

- second, I needed to add a policy file in /etc/dbus-1/system.d/. I found an example on [http://kkaempf.blogspot.com/2009/02/driving-d-bus-with-ruby.html](http://kkaempf.blogspot.com/2009/02/driving-d-bus-with-ruby.html)


After getting these two things right, I was able to setup my service and access it through my cgi script :-)



Peter

---

