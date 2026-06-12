---
title: "dbus listing interface functions"
date: 2008-06-12
forum: Programming Talk
---

### Post by scicode on 2008-06-12
i got to a point where i can see all available dbus interfaces (sry if i do not use the correct ligu) with 
```
dbus-send --session --type=method_call --print-reply --dest=org.freedesktop.DBus /org/freedesktop/DBus org.freedesktop.DBus.ListNames
```

but how do i get dbus-send to show all available methods of an interface. this has to be possible somehow

---

### Post by deuce868 on 2008-06-12
Check out d-feet. It's an app that will list available dbus calls and such on your system. You could check out the code they use to help you get going from there. 
[https://hosted.fedoraproject.org/projects/d-feet/](https://hosted.fedoraproject.org/projects/d-feet/)

---

### Post by scicode on 2008-06-16
Thank you deuce868, just what i needed

---

