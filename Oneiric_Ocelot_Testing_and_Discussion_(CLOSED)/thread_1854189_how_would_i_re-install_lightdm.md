---
title: "how would i re-install lightdm"
date: 2011-10-03
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rburkartjo on 2011-10-03
messing around with xfce in 11.10 and set my computer so it will not boot into lightdm as default. cant get any where can get to a terminal in recovery mode but in my daughter's desktop or can use ctrl+alt+f2 to get into mine. how would i reset. note i cant get into the startup screen that enables you to start unity, gnome 3, unity2 or xfce sessions. if i could get this back could fix. any ideas. leave it to me to pouch things so close to the final release. tks

---

### Post by rburkartjo on 2011-10-03
had to boot up into my linux mint partition.

---

### Post by crdlb on 2011-10-03
I'm a little unclear, but if you can get to a terminal, ensure that lightdm is installed, and if so, try: ```
sudo dpkg-reconfigure lightdm
```

---

### Post by rburkartjo on 2011-10-03
crd tks that did the trick

---

