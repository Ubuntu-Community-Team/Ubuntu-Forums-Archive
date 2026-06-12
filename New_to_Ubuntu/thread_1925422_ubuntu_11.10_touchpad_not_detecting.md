---
title: "ubuntu 11.10 touchpad not detecting"
date: 2012-02-14
forum: New to Ubuntu
---

### Post by satyapramodh on 2012-02-14
i used ubuntu 11.04 before but in my recent fresh install my touchpad is not even detecting. Its working with External mouse. its synaptics mouse. my touchpad is working in my windows 7. Also i dont see my battery status/symbol anymore. please help me guys.
my lappy is Dell inspiron n5010 n i use ubuntu 11.10 64bit.

---

### Post by dspi on 2012-02-19
Have you tried this:
```

synclient TouchpadOff=0

```

---

### Post by Blueyak on 2012-02-19
I have an Acer Aspire One 722 netbook and the command dspi mentions allows me to turn my touchpad on.  Turn touchpad off again with the following. ```
synclient TouchpadOff=1
```
When I was using Ubuntu 11.04 and the panel did funky things (like icons disappearing), I used the following command to restart the panel.```
killall gnome-panel
```

---

