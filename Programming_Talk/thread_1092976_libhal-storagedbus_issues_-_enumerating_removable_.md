---
title: "libhal-storage/dbus issues - enumerating removable drives"
date: 2009-03-11
forum: Programming Talk
---

### Post by twiddle87 on 2009-03-11
Just wondering if anyone out there has some good information on how to use libhal/libhal-storage? I've been muddling through the headers and ive got 

```
DBusError myError;
LibHalContext * myContext = libhal_ctx_new();
libhal_ctx_init(myContext, &myError);
//LibHalDrive* myDrive = libhal_drive_from_device_file(myContext,"/dev/sda");
```

however for some reason the commented line causes

```
process 2313: arguments to dbus_connection_send_with_reply_and_block() were incorrect,
 assertion "connection != NULL" failed in file dbus-connection.c line 3298.
```

Can anyone explain why im getting this error? using 'sudo invoke-rc.d [dbus/hal] status' ive made sure both are running. It may be simply im not initializing part of the library before trying to use it, but the headers dont exactly make things clear... eventually i would like to enumerate through the mounted drives on the system and filter the removable ones from that list.

---

