---
title: "How Identify Optical Disk Device?    Model, Capabilities, Compaibilities."
date: 2013-11-08
forum: New to Ubuntu
---

### Post by TomBrooklyn on 2013-11-08
How can one identify the optical disk installed in a computer running Ubuntu?


It is desired to identify the manufacturer, model, and if possible, the capabilities and compatibilities of the device.

---

### Post by newb85 on 2013-11-08
I would start here:
```
sudo lshw -C disk
```

---

