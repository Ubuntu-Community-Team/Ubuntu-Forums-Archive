---
title: "Desktop is not at the center after nvidia driver installation"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cmfrtblynmb on 2011-10-01
Hello all

The title was a little weird, sorry about that

Here is the very quick description: After installing nvidia driver, my desktop has shifted a little southeast! Just check the pic: 

[http://i.imgur.com/Yr5Sr.jpg](http://i.imgur.com/Yr5Sr.jpg)

(edit: sorry about the picture size. I really could not resize it) 

As you can see desktop area is not centered (although unity panels are at their correct place)

I also installed drivers directly from Nvidia, nothing changed. Now I uninstalled all Nvidia drivers and reinstalled Nouveau ones, still I have the same problem (maybe I was not able to reinstall Nouveau drivers, I am not sure about that one)

2D desktop does not have this problem

Thanks

---

### Post by cariboo on 2011-10-01
Make sure you are using an up-to-date server, and update Unity to 4.20.0-0ubuntu2, that should solve your problem. To find what version you are using in a terminal type:

```
unity --version
```

---

### Post by cmfrtblynmb on 2011-10-01
It is the current version

I have tried everything, I installed, uninstalled all nouveau, nvidia drivers possible. The desktop area is always shifted.

---

### Post by MacUntu on 2011-10-01
This is no graphics driver problem. You need Unity version 4.20.0-0ubuntu2.

Check that via typing 'apt-cache policy unity' in a terminal.

---

### Post by cmfrtblynmb on 2011-10-01
Thanks for the replies

I already have unity 4.20.

The problem is now fixed after I installed gnome-shell, logged into gnome desktop then logged back into unity

I am using nividia drivers from nvidia site. 

But now I get 1024*768 resolution everytime I log in. I have to change resolution from nvidia-server settings. I have modified xorg.conf to get 1920*1080 but nothing changed

---

