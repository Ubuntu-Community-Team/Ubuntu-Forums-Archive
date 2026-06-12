---
title: "&quot;umount&quot; without being root"
date: 2007-10-08
forum: Programming Talk
---

### Post by Kenobi on 2007-10-08
hi,

nautilus unmounts every device whatever simply by rightclicking it and choose "unmout device" - no need for any root.

But when I try to do the same on the command line (using the command "umount" it only works with super user rights (sudo)

Is there a command-line way that works without being root?

---

### Post by Ramses de Norre on 2007-10-08
That is done by HAL (Hardware Abstraction Layer) by sending an appropriate message through DBUS (a system messaging system).

For example, to unmount my home partition I'd invoke this:
```
dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/volume_uuid_a5ea6ca9_485c_4e0f_95b3_ea85324403e2 org.freedesktop.Hal.Device.Volume.UnMount
```
You'll need to know the UID for the partition and have access to the system message bus.

---

### Post by Kenobi on 2007-10-09
Sounds great. But how can I retrieve the UIDs - "mount" doesn't seem to display them!?

---

### Post by Ramses de Norre on 2007-10-09
You can use this to retrieve the UID for /dev/sda1 (as example):
```
ls -la /dev/disk/by-uuid/|grep sda1|cut -d' ' -f8
```
There might be cleaner ways and HAL might accept the volume-id or path to the device directly but I can't find proper documentation on it.
I hope this works for you.

---

### Post by Kenobi on 2007-10-12
hi!

Your second tip worked wonderful (I only had to replace -f8 with -f9) - I can get all the uuids now.

But the dbus-send doesn't work at all. I tried to unmount my stick, and this is what I got in the terminal:

[FONT="System"]dbus-send --system --print-reply --dest=org.freedesktop.Hal /org/freedesktop/Hal/devices/volume_uuid_46BD-ECFD org.freedesktop.Hal.Device.Volume.UnMount
process 7572: arguments to dbus_message_new_method_call() were incorrect, assertion "_dbus_check_is_valid_path (path)" failed in file dbus-message.c line 1074.
This is normally a bug in some application using the D-Bus library.
process 7572: arguments to dbus_message_set_auto_start() were incorrect, assertion "message != NULL" failed in file dbus-message.c line 2462.
This is normally a bug in some application using the D-Bus library.
Couldn't allocate D-Bus message
[/FONT]

---

### Post by winch on 2007-10-13
For devices like usb sticks that appear in /media you can use eject to unmount them.

```

eject /media/disk/

```

---

### Post by vanadium on 2007-10-13
or

pumount

to just unmount them.

---

### Post by Kenobi on 2007-10-14
Hi,

thanks alot! - Eject and pumount are just what I needed! Actually both even work for  hard drives -  ok eject displays an error message but who cares - my hard drives are irreversibly unmounted :-) 

The funny bit is that as though I can eject and pumount my hard drives being "user", I can't mount or pmount them - mount sais, you need to be root, pmount sais: "this is not an exchangeable media [this means. a hard drive]"

Any ideas on this?

---

