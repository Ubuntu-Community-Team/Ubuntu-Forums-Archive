---
title: "Right Click"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by Anoop Bharawaj on 2012-10-30
I Have a lenovo z580 laptop.
The right click button doesnt function in ubuntu 12.4.
As the laptop driver given to me only work for Windows,I dont know what to do.
Need Help 
:confused:

---

### Post by wolfinio on 2012-10-30
> **Anoop Bharawaj said:**
> I Have a lenovo z580 laptop.
The right click button doesnt function in ubuntu 12.4.
As the laptop driver given to me only work for Windows,I dont know what to do.
Need Help 
:confused:

you should or search on internet for the right driver or just connect a mouse ....

---

### Post by mahdiolfat on 2012-10-30
Try this, should work:

```

sudo su

``````

echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe

``````

shutdown -r now

```

---

### Post by Frogs Hair on 2012-10-30
Install the Gnome Tweak Tool if not already and under the desktop section make sure " have file manager handle desktop" is enabled.

---

