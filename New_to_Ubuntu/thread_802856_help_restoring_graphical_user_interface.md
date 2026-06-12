---
title: "help restoring graphical user interface"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by amgc5 on 2008-05-21
for some strange reason, I decided to disable the GUI under

System> administrator>services

As a result, Ubuntu now loads into a shell/text based interface. I can still login using my username and password, but not sure how to navigate to restoring the GUI on Ubuntu Hardy.

Can someone provide a step by step approach to restoring it?

Thanks!

---

### Post by aktiwers on 2008-05-21
Type:
```
startx
```

And enable the gui again.

---

### Post by amgc5 on 2008-05-21
This is awesome...I got in.

Can I re-activate the Graphical user login in the services menu? While doing that, I received a blue screen taking about X server being active?

---

### Post by aktiwers on 2008-05-21
I think that is because you disabled the graphical LOGIN and gdm (graphical user interface) is still running in the background. The startx command tries to open a new one, and thats whey it said its already active.

If you enable it again in services then all should be back to normal after reboot.
If you don't want to reboot you can logout (this will take you back to fullscreen terminal) and type:

```

sudo /etc/init.d/gdm stop

```
and then:
```

 sudo /etc/init.d/gdm start
 
```

Done! :)

---

