---
title: "monitor brightness"
date: 2013-05-15
forum: New to Ubuntu
---

### Post by senorian on 2013-05-15
xubuntu.12.04.2. desktop.64 bit.
On April 12 I did an update which changed the Nvidia dispay and I lost my ability to reduce (change) the screen brightness.
I have posted this problem on the multimedia section and on the distribution section .
No rsponses
please help
thank you

---

### Post by Nolix on 2013-05-15
see if your birghtness control is activated in your xorg.config file. 
```
cd /etc/X11/
```

then open your xorg.config in gedit or your default text editor:
```
sudo gedit xorg.conf
```

look for 

```
 Option         "RegistryDwords" "EnableBrightnessControl=1"
```

in the section that identifies your nvidia graphics card

if it isn't there edit it accordingly, restart and see if that enables it.

---

