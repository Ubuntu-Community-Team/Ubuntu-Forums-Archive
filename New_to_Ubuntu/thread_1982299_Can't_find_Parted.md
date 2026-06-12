---
title: "Can't find Parted"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by s1wood on 2012-05-18
I want to repartition an external drive. 
Software centre says GNU Parted installed, can't find it, Synaptic says not installed: have installed it but still can't find it.

Where should I be looking? This is 11.04 with gnome desktop.

Susan

---

### Post by plucky on 2012-05-18
> **s1wood said:**
> I want to repartition an external drive. 
Software centre says GNU Parted installed, can't find it, Synaptic says not installed: have installed it but still can't find it.

Where should I be looking? This is 11.04 with gnome desktop.

Susan

Type **gparted** into a terminal window.

It might be under **System > Administration**

---

### Post by sikander3786 on 2012-05-18
From a Terminal, try:

```
sudo apt-get install gparted
```

What does it say?

And what if you press "Alt + F2" and type:

```
gksu gparted
```

---

### Post by kc1di on 2012-05-18
if you installed gparted just look for in in Dash hud by typing gparted it should come up. in fact when I type the first two letter it shows on my machine. 
if that doesn't work reinstall gparted.

---

### Post by Cheesemill on 2012-05-18
parted is a command line tool, it doesn't have a graphical interface which is why you can't find it in a menu anywhere.

As others have mentioned above install gparted and use that instead.

---

### Post by s1wood on 2012-05-18
Thank you all,
gparted installed from the terminal and is now found in System-Administration.

Still don't know why the Spftware centre said I had it though.

Thanks again for rapid response.

Susan

---

