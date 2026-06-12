---
title: "bluetooth disable"
date: 2013-03-04
forum: New to Ubuntu
---

### Post by tendouser on 2013-03-04
disable bluetooth at startup under quantal?

cheers

---

### Post by cortman on 2013-03-04
Do you want to disable the bluetooth module in the kernel, or keep gnome-bluetooth applet from starting?

---

### Post by tendouser on 2013-03-04
applet from starting

cheers

---

### Post by carl4926 on 2013-03-04
Dash > Startup Applications

---

### Post by tendouser on 2013-03-04
i see nothing at startup applications ...the box is empty!

---

### Post by fantab on 2013-03-04
All auto-start apps don't show up in the 'Startup Applications' these days. To reveal all the auto-start applications run the following in the terminal:


```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

After they are revealed just **uncheck** all those apps you don't want to auto-start.

---

### Post by carl4926 on 2013-03-04
> **fantab said:**
> All auto-start apps don't show up in the 'Startup Applications' these days. To reveal all the auto-start applications run the following in the terminal:


```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```

After they are revealed just **uncheck** all those apps you don't want to auto-start.

Nice tip

---

### Post by tendouser on 2013-03-05
yes thanks for sed command!

---

