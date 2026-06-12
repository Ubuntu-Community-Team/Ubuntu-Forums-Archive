---
title: "New monitor"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by iPhQ on 2011-12-16
Today I have bought a new monitor.
I have tried to make it a dual monitor by using my nVidia settings but I failed. However somehow I managed to make it the primary screen, but for example when I maximize my google chrome I can't see the tabs because the menu at the top is blocking it.
How can I fix this?
And how can I get dual monitor support?
Also when I turn my computer on my speakers kind of make a pop/crack sound and it sounds similar when I login to skype.
Is there a way to fix this?

---

### Post by wolfen69 on 2011-12-16
Are you starting nvidia settings as superuser? You need to do:
```
gksu nvidia-settings
```
make your changes, hit apply, then save to X. Sometimes the primary monitor won't be right at first, just close nvidia settings and restart it.

---

### Post by iPhQ on 2011-12-16
> **wolfen69 said:**
> Are you starting nvidia settings as superuser? You need to do:
```
gksu nvidia-settings
```
make your changes, hit apply, then save to X. Sometimes the primary monitor won't be right at first, just close nvidia settings and restart it.

I did it but the new screen is white. Most probably because it's not primary. I have tried restarting the computer.


EDIT:: Nevermind. I have set it as twinview and it worked.

---

### Post by iPhQ on 2011-12-16
When I restarted my computer I got this error message:
```

Could not apply the stored configuration for monitors
none of the selected modes were compatible with the possible modes:
Trying modes for CRTC 354
CRTC 354: trying mode 3200x1080@50Hz with output at 1024x768@50Hz (pass 0)
CRTC 354: trying mode 3200x1080@50Hz with output at 1024x768@50Hz (pass 1)
```
How can I fix this?
It has happened when I switched sides with monitors.

---

