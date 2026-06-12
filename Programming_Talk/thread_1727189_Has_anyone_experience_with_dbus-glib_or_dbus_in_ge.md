---
title: "Has anyone experience with dbus-glib or dbus in general?"
date: 2011-04-12
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2011-04-12
Hello,

here's my problem. 

I have a program that utilizes dbus-glib. Many instances can be created at a time. The program behavior is this. The first instance creates a bus-name in the session bus and becomes the PRIMARY instance. The other instances call methods on the first instance through dbus. This works well, but I want to solve a corner-case problem.

If my first instance dies/exits/quits then I want one of my other instances to take the bus-name(recreate it actually) and become the PRIMARY instance. My problem is how do I 'watch' a bus name? How do I get notified if a bus name disappears?

ps: I don't want to rely on signals emitted by the PRIMARY instance that it will exit/quit, because A)I think that these don't work asyncronously and B)if the PRIMARY instance crashes no signal will be emitted.

Thanks in advance.

---

### Post by SledgeHammer_999 on 2011-05-08
Ok. I found the solution.

When you request a bus-name that already exists, D-Bus puts your application in a queue for that name. Unless you pass specific flags during the request telling it otherwise.

So when the PRIMARY instance of my application exits/dies/crashes/quits D-Bus automatically gives the bus-name to ONE of the other applications/instances that requested it and are in the queue.

So how do you get informed that you now own the bus-name? Easy, connect to the bus signal called "NameAcquired".

Info about the queue-> [here](http://dbus.freedesktop.org/doc/dbus-specification.html#message-bus-names) (read the documentation of **org.freedesktop.DBus.RequestName**)
Info about the NameAcquired -> [here](http://dbus.freedesktop.org/doc/dbus-specification.html#message-bus-messages) and look for **org.freedesktop.DBus.NameAcquired**

---

