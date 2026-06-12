---
title: "python-dbus error: 'SessionBus' object has no attribute 'get_service'"
date: 2007-01-25
forum: Programming Talk
---

### Post by st00ner on 2007-01-25
Well im trying to run the following script(to announce my muine song in xchat), but it wont work. the exact error is:
AttributeError: 'SessionBus' object has no attribute 'get_service'
for the line:
muine_service = bus.get_service("org.gnome.Muine")

I googled and searched the forums, but with no luck. There were no complaints on this exact script... im really confused. here is the script:

[http://www.xs4all.nl/~basvdlei/python/m_announce.py](http://www.xs4all.nl/~basvdlei/python/m_announce.py)

My python version is 2.4.4~c1-0ubuntu1 (edgy)
My python-dbus version is 0.71-2ubuntu1 (edgy)
my dbus version is 0.93-0ubuntu3.1 (edgy-security)

any ideas? to test if the code works on works on your machine, in python run this script:
import dbus
bus = dbus.SessionBus()
muine_service = bus.get_service("org.gnome.Muine")

i really dont know why it wont work, but on the forums it looked like alot of people had issues with dependencies on python-dbus on edgy.  Is there some reason it should just not work? i have tried similar scripts to this one that use python-dbus, and non of them work. any help/hacks would be great. I really think this is a dependency/version confliction, but its relavent to python which im am pretty fluent in so i posted it here.

---

### Post by st00ner on 2007-01-27
bump :[. anyone expereince python-dbus problems or dbus compatibility issues like this?

---

### Post by tweedledee on 2007-02-06
> **st00ner said:**
> bump :[. anyone expereince python-dbus problems or dbus compatibility issues like this?

Yes.  And after a great deal of effort and poking around example files and the limited documentation I could find, I have no explanation at all for why the script you are referring to doesn't work (won't for me either, nor will any that relies on get_service).  However, the information and examples here may serve as new starting point: [http://gitweb.freedesktop.org/?p=dbus/dbus-python.git;a=tree](http://gitweb.freedesktop.org/?p=dbus/dbus-python.git;a=tree).  The example/example-signal-recepient.py is probably the closest example to what you want to do, although you'll probably have to play with it quite a bit.  The doc folder does have a little helpful information as well.  Basically, it seems that in some recent release, everything was fundamentally changed and not noted (at least in a way that makes senses to us poor end-users), and no good documentation exists.

---

### Post by tweedledee on 2007-02-06
More success.  Try replacing these lines:```
muine_service = bus.get_service("org.gnome.Muine")
player = muine_service.get_object("/org/gnome/Muine/Player","org.gnome.Muine.Player")
  
``` from your linked site to these:```
player = muine_service.get_object("org.gnome.Muine.Player","/org/gnome/Muine/Player")
muine_service = dbus.Interface(player, "org.freedesktop.Muine.Player")
```
At least, an equivalent solution worked for me.  It appears that the "Interface" approach has replaced the "get_service" approach, which also requires that "get_object" come first instead of second.

---

