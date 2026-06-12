---
title: "GIMP error; menu bar options grayed-out, can only use shortcuts"
date: 2014-01-11
forum: New to Ubuntu
---

### Post by tfglynn on 2014-01-11
**Edit: **The problem also affects other apps.
Hello, I'm running the latest version of GIMP on saucy. After attempting to install the GNOME Shell yesterday, I ran into a number of problems, among them this: I can open GIMP, but I cannot do anything via the menu bar. I can open files with it, I can use keyboard shortcuts, and I can draw, but that's all. When I open GIMP via the terminal, I get the following message:
```

(gimp:2444): Gimp-Widgets-CRITICAL **: gimp_device_info_set_device: assertion '(info->device == NULL && GDK_IS_DEVICE (device)) || (GDK_IS_DEVICE (info->device) && device == NULL)' failed

```
The 4-digit number at the beginning seems to change every time, but the rest stays the same. I've tried uninstalling GIMP (sudo apt-get remove --purge gimp) and reinstalling, but that didn't fix the issue. I have no idea what the error message means, so I'm hoping someone here will. Any help is appreciated.

---

### Post by king.of.random on 2014-01-11
Not sure how to help as I'm using Unity. But have you tried right clicking on you work space as this usually brings up the menu?

---

### Post by tfglynn on 2014-01-11
Right-click works just fine. Thanks for telling me this; now GIMP isn't totally unusable. :grin: But the menu bar still isn't working. Also, I switched back to Unity before encountering this problem.

---

### Post by Frogs Hair on 2014-01-11
I notice this when working with some, but no all clip-art, usually when layering . The right click method gets the job done though and looking at the properties of the clip-art indicates  nothing unusual.

---

### Post by tfglynn on 2014-01-11
I found out just now that the menu bars on other apps (e.g. Banshee, LibreOffice) are also not working. Didn't notice before since I don't use those menus often. Still haven't found a solution yet.

---

### Post by Menno124875 on 2014-01-31
I have the same problems. Hope someone comes up with a fix quickly.

---

### Post by sandyd on 2014-01-31
Hi, this sounds like a bug, can you report a bug please?

Instructions [here]("https://help.ubuntu.com/community/ReportingBugs")

---

