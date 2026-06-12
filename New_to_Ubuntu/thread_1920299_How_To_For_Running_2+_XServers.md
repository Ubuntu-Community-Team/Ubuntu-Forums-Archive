---
title: "How To For Running 2+ XServers"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by rgreener25 on 2012-02-04
Does anyone know a good how to on how to run 2 xservers?

---

### Post by Mahkoe on 2012-02-04
[http://lmgtfy.com/?q=run+2+x+servers+ubuntu](http://lmgtfy.com/?q=run+2+x+servers+ubuntu)

Or, if you don't want to read, here's my own quick guide:
first, edit the xwrapper file:
```
sudo gedit /etc/X11/Xwrapper.config
```
And change it to allowed_users=anybody.
Now, edit your .xinitrc file in your home folder so that it runs any program you would like, mine starts wmii; a lightweight window manager. If you have xfce4 installed, you can edit your .xinitrc file to start it. Ex:
```

startxfce4

```
```

wmii

```
(It doesn't look like much, but that's all you need to put in the file)
Then, open up a terminal and type 
```

xinit -- :2

```
Please note that I've never been able to start another gnome session, and I don't think you can without considerable modification and effort.

Cheers

EDIT:
You can switch back to the first x server by pressing ctrl alt F7, and to the new one with ctrl alt F8, and if you have third ctrl alt F9... I think you get the point

---

