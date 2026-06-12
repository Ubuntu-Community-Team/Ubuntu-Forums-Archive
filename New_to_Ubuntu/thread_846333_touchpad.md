---
title: "touchpad"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by king18 on 2008-07-01
the side of my touchpad usually allows me to scroll down with just sliding my finger blah blah.....its not doing it now...and its not that im not doing it right ive been trying for like 5 minutes now.....

---

### Post by avtolle on 2008-07-01
This is from memory; System>>Preferences>>Mouse, click on the touchpad tab, and see if somehow this option has become inactivated.

---

### Post by king18 on 2008-07-01
there isnt a touchpad tab..

---

### Post by tjwoosta on 2008-07-01
it is a synaptics touchpad?

the problem you are describing happened to me in windows vista when i didnt have the touchpad driver installed

i think the same must be happening to you 

the  thing is, i think ubuntu comes with the synaptics drivers preinstalled

---

### Post by king18 on 2008-07-01
now that you say that i just uninstalled that on accident.....thaank you

---

### Post by king18 on 2008-07-01
i have vista do you know how i can reinstall it?

---

### Post by fiddledd on 2008-07-01
> **king18 said:**
> i have vista do you know how i can reinstall it?

You can get the drivers for Vista here:

[http://www.synaptics.com/support/drive.cfm](http://www.synaptics.com/support/drive.cfm)

---

### Post by tjwoosta on 2008-07-01
yea the vista drivers are at the synaptics website

but if your looking for the ubuntu drivers you can get it from the package manager (just search synaptics and its like the last one in the list

says 

xserver-xorg-input-synaptics

so just do 

```
sudo apt-get install xserver-xorg-input-synaptics
```

---

