---
title: "terminal command to trigger restart/shutdown menu"
date: 2014-05-11
forum: New to Ubuntu
---

### Post by gychang2 on 2014-05-11
what is the terminal command to trigger start of the menu?

thanks in advance.

---

### Post by matt_symes on 2014-05-11
Hi

Try these 

Under Unity or Gnome-shell

```
gnome-session-quit
```

Under Xubuntu

```
xfce4-session-logout
```

Under Lubuntu try

```
lxsession-logout
```

I'm not sure how under Kubuntu.

Kind regards

---

### Post by philinux on 2014-05-11
Look at the man pages for gnome-session-quit

---

### Post by veddox on 2014-05-11
Do you need to launch the GUI menu? If not, you can use these two commands straight from terminal:

shut down:
```
sudo shutdown -h now
```

reboot:
```
sudo reboot
```

---

### Post by matt_symes on 2014-05-11
Hi

> Do you need to launch the GUI menu? If not, you can use these two commands straight from terminal:

This is very true; it will shutdown Linux.

However, it would be remiss not to point out that shutting down Linux this way will not save any session data, should that be what you are trying to achieve.

Kind regards

---

### Post by veddox on 2014-05-11
> [COLOR=#000000]However, it would be remiss not to point out that shutting down Linux this way will not save any session data[/COLOR]

Thanks for adding that, I hadn't realized that that was the case :-)

---

### Post by Paulgirardin on 2014-05-11
The command below will give you a menu with lock,suspend,restart,shutdown options.

```
gnome-session-quit --power-off
```

---

### Post by gychang2 on 2014-05-11
thanks for all the input, gnome-session-quit --reboot works perfectly.

---

