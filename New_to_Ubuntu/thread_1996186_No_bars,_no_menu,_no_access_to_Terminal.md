---
title: "No bars, no menu, no access to Terminal"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by ubujt on 2012-06-04
I tried to install Lubuntu. Ubuntu is the system I already had.

After the installation, my computer took me to the Lubuntu log-in screen (under Ubuntu I didn't have a log-in screen).

When I try to log in an error message comes up saying there are too many instances, and then it loads the desktop screen like normal.

The problem is that the upper and lower bars, whatever they're called, do not show up. That means no tabs, no menus, no Terminal, no Firefox.

I can click on the Desktop items and open them, but I can't go online or do anything needing a program icon.

How can I fix this?

I am very frustrated with Ubuntu right now. I am posting this from Vista right now.

---

### Post by Senior_Buckethead on 2012-06-04
Why did you install Lubuntu when you had ubuntu? Is your system low RAM?

Anyhow, I think your problem stems from the window manager you are using, I can only think that during your upgrade something go mixed up. Try reinstalling LXDE (which is the default window manager for Lubuntu. (you'll have to be running live cd, someone more knowledgeable can help you here)

[http://lxde.org/lxde](http://lxde.org/lxde)

Don't give up on Ubuntu/Lubuntu, just persevere and you will get there.
Sorry I couldn't be more help.

---

### Post by Palanthas on 2012-06-04
Sadly I can't help you completely fix this issue but maybe this will help you some...

This will take you to a terminal even if you can't get to anything on the desktop.
```
CTRL+ALT+F1
```
You can use F1-F4.

This will take you back to the desktop.
```
CTRL+ALT+F7
```

---

### Post by bruno9779 on 2012-06-04
Follow phalantas advice and press:

```
Ctrl + F1
```

Then restart lxde x server:

```
sudo service lxdm restart
```
or
```
sudo /etc/init.d/lxdm stop
```

If it doesn't work yet, use the Ctrl+F1 terminal to install a different desktop environment.

---

