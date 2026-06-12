---
title: "Low Graphics Mode AHHH!!!!"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by ranger5664 on 2008-10-04
I am running xubuntu hardy and i have finally gotten my graphics drivers for my outdated graphics driver to work. kinda... I have an NVIDIA Geforce3 Ti200, and a view Sonic m70 monitor. I have two 40 gb harddrives, and idk how much ram, but probably a gig. I have installed my graphics driver and rebooted and i ended up in low graphics mode and dont know how to configure it so that i can get out of low graphics mode. Can anyone help?

---

### Post by jrothwell97 on 2008-10-04
My first suggestion would be for you to run

```
sudo dpkg-reconfigure xorg
```

at a terminal and see what happens.

---

### Post by ranger5664 on 2008-10-04
tried that it didnt work. but thanks.

---

### Post by roger_1960 on 2008-10-04
Hi

Try sudo displayconfig-gtk . Then change the model and then resolution until it works. You may have to log out and then in again for changes to happen.

---

