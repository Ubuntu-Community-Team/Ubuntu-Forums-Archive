---
title: "DBus interface docs for Gnome?"
date: 2007-01-25
forum: Programming Talk
---

### Post by WakkiTabakki on 2007-01-25
Hi all
I've been scouting the net for a list of supported D-Bus methods for Gnome, but haven't found any... 
Specifically, I'd like to be able to restart X (no problem) and have Gnome restore the current session next time it starts and then go back to the default session. This is all to be done from Python.

Can someone point me a direction?

Cheers
/N

---

### Post by tweedledee on 2007-02-06
> **WakkiTabakki said:**
> Specifically, I'd like to be able to restart X (no problem) and have Gnome restore the current session next time it starts and then go back to the default session. This is all to be done from Python.

Can someone point me a direction?


I've no idea if this will give you enough information to do what you want, but here is the only documentation I've been able to find on python and dbus: [http://gitweb.freedesktop.org/?p=dbus/dbus-python.git;a=tree](http://gitweb.freedesktop.org/?p=dbus/dbus-python.git;a=tree).  Between the limited information in the doc folder and the example files, I'm beginning to understand what can and can't be done, but I haven't come across anything that describes quite the behavior you are requesting.  This is all very incomplete, but somewhat better than nothing.

---

