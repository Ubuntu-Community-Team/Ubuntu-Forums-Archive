---
title: "simple temperature monitor in tray like ktemperature but for gnome&gt;"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-11-03
What's a good simple temperature monitor in the tray like ktemperature but for gnome?

---

### Post by racmar on 2008-11-03
```
sudo apt-get install sensors-applet
```

then right-click on the panel and choose "add to panel", and pick "hardware sensors monitor"

---

### Post by Bodha on 2008-11-04
That worked fast thanks but Im only getting up the GPU . Im new to Linux running Ubuntu 8.04 on a MoBo with full sensors - the Asus P5K-E. Any suggestions?

---

### Post by racmar on 2008-11-04
try this:
```
apt-cache search sensors
```

look at the package names and try installing some of the lib sensors stuff.  Then restart gnome-panel and see if you have more choices.

eg:
```

sudo apt-get install lm-sensors libsensors3 libsensors4

```

---

