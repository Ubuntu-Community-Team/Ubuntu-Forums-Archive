---
title: "GUI real beginner questions"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by mac-i-bear on 2008-10-28
newbie and neophyte - finally got server installed and running and i can logged in so far - trying to learn in baby steps...
(1) is there a GUI for the server ?
(1.1) how can i install it (step by step please) and
(1.2) do not want to launch it automagically at start up so how can i launch it when i need it

---

### Post by DGortze380 on 2008-10-28
> **mac-i-bear said:**
> newbie and neophyte - finally got server installed and running and i can logged in so far - trying to learn in baby steps...
(1) is there a GUI for the server ?
(1.1) how can i install it (step by step please) and
(1.2) do not want to launch it automagically at start up so how can i launch it when i need it

1) Yes, pick one. gnome, kde, xfce, fluxbox...
1.1) sudo apt-get install ubuntu-desktop
(or kubuntu-desktop, or xubuntu-desktop, or xorg && fluxbox)
1.2) will need to modify a few things to make it not start automatically, not sure exactly what, but it's doable. To launch a GUI on your system type: startx

---

### Post by namegame on 2008-10-28
The server can run any possible GUI configuration. Gnome, KDE, XFCE, LXDE, OpenBox, Fluxbox, etc. I would suggest something as lightweight or lighter than XFCE.

For instructions on how to install each:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Look in the links under the "Playing around" section.

---

### Post by cariboo on 2008-10-28
To stop the gui from starting automatically at the command prompt type:

```
sudo update-rc.d -f gdm remove
```

This will stop the Gnome Desktop Manager from starting.

An other option, if you don't want to load a gui all the time is to use Webmin. It is available here:

[http://www.webmin.com/](http://www.webmin.com/)

Have a look around as they have a demo server set up. Sort of try before you download. :)

Jim

---

