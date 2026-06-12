---
title: "GUI for server 8.04"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by andyinjapan@hotmail.com on 2008-05-14
Dear all,
Where can I get A GUI for the server edition?
Many thanks
Newbie

Andy

---

### Post by Monicker on 2008-05-14
```
sudo apt-get install ubuntu-desktop
```

or kubuntu-desktop, if you prefer

---

### Post by billgoldberg on 2008-05-14
or xubuntu-desktop

to keep things light

---

### Post by lazyart on 2008-05-14
Keep in mind that using a GUI on a server is generally discouraged.  It a lot easier to configure-- can't deny that.  Hopefully once you've got it set up you can remove the GUI and switch to webmin-- a web interface for configuring the server.

---

### Post by hyper_ch on 2008-05-14
> **lazyart said:**
>  It a lot easier to configure-- can't deny that.
Sure I can :) Editing config files in a another GUI than the CLI is not different ;)

---

### Post by Joeb454 on 2008-05-14
Personally, if you wanted a gui, I wouldn't install one of the Desktop meta-packages.

I'd install xserver-xorg, and then install a very lightweight WM such as Fluxbox

---

### Post by cwgatling on 2008-05-14
Me too. xserver-xorg and gedit for a server and I'd be happy. You get a lot of unnecessary stuff with the desktop packages.

---

