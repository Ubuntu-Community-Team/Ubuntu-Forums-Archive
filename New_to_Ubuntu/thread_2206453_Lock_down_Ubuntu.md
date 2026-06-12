---
title: "Lock down Ubuntu"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by david165 on 2014-02-19
Hello Guys,
Hope you can help I have tasked with getting a ubuntu build set so that it can be used for a thin client to Windows 7 however I have also been asked to lock it down as best as I can.

I have done alot of digging and everyone says get [http://www.unixmen.com/install-lockdown-editor/](http://www.unixmen.com/install-lockdown-editor/) however whilst this looks great its not available anymore saying its built into Gnome 3+

Is there any other alternatives like Lock down Editor that can do the job for me?

---

### Post by TheFu on 2014-02-19
Never heard of "lock down editor" and ubuntu is sorta heavy for this specific usecase.
Get the 12MB (yes, that is MB) version of TinyCore.  It comes with minimal apps. Install the RDP client app that you like. On exit, save the data.  Now you have a highly limited Liunx install probably 20MB tops that does 1 thing - thin client.

If there aren't any apps, it is hard to misuse the OS. If the only app installed is a thin client ... that will be it.

Oh - and Gnome3 is a hog. Not exactly what is needed for limited GPU systems, netbooks, and cheap notebooks like are sold these days.

I use TinyCore in a VM for my online financial needs.  Boots up in 2 seconds - literally. Fresh with every boot, cause I never save my session at exit.

If you insist on using Ubuntu - use the alternate installer, install an extremely limited set of packages (Pure WM is best, definitely NO DE) and do not setup any local accounts for users. They will use the "guest" account only. That way, anything they save to HOME will be wiped at logout.

---

