---
title: "login page"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by 2k! on 2008-06-02
hey, i have a problem. i was bored so i decided to set a new login page. it didnt work so i uncheck the other two and just check the one i wanted. well now the tan screen pops up and just loads indefinetly. i am using hardy heron. is there a way to solve this as i can still access the terminal with ctrl alt f1. thanks alot.

---

### Post by Yuki_Nagato on 2008-06-02
Are you able to get to a terminal using Alt+Ctr+F1 for instance?

---

### Post by 2k! on 2008-06-02
yes i am.

---

### Post by Yuki_Nagato on 2008-06-02
Try logging in though that and then entering 

```
sudo /etc/init.d/gdm stop
```

to kill the X process.

then try

```
xstart
```

to hopefully start the X process over.  (X is the GUI skeleton for GNOME or KDE)

---

### Post by 2k! on 2008-06-02
>  ```
xstart
```

xstart: command not found.

---

### Post by Maestro23 on 2008-06-02
Try:

> startx

---

### Post by tigersrock on 2008-06-02
Use ```
startx
```

---

### Post by Yuki_Nagato on 2008-06-02
> **Maestro23 said:**
> Try: startx

*Facepalm

Thank you for picking up on that.

---

### Post by 2k! on 2008-06-02
ok guys thanks im in, but now i went to 
```
sudo gdmsetup
``` to fix it and this popped up. 

gdm is not running you may be running something like kde. how do i fix this to be back in gnome to fix it?

---

