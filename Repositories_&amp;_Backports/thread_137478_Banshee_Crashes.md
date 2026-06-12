---
title: "Banshee Crashes"
date: 2006-02-28
forum: Repositories &amp; Backports
---

### Post by DanielPal on 2006-02-28
Hi I am kind of new to ubuntu, right know everything seems to work fine except banshee.
When runned:
```
daniel@home:~$ banshee

Unhandled Exception: DBus.DBusException: Unable to determine the address of the message bus
in [0x0003e] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:46) DBus.Bus:GetBus (BusType busType)
in [0x00001] (at /build/buildd/dbus-0.36.2/mono/Bus.cs:23) DBus.Bus:GetSessionBus ()
in [0x00007] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/DBusIPC.cs:53) Banshee.DBusServer:.ctor ()
in [0x00016] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:135) Banshee.Core:.ctor ()
in [0x0000b] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Core.cs:73) Banshee.Core:get_Instance ()
in [0x000ef] (at /build/buildd/banshee-0.9.7.1+cvs20051004+revertedto0.9.7.1/src/Main.cs:78) Banshee.BansheeEntry:Main (System.String[] args)
```

I checked all dependencies and everything is fine. Can someone point me out how to fix this ?
-daniel
EDIT: By the way I am using kubuntu breezy badger

---

