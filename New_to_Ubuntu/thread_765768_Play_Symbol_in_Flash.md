---
title: "Play Symbol in Flash?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by The Cake is a Lie on 2008-04-24
Every time I am on a website with Flash, such as YouTube, there is a big Play symbol over it. I have to press it in order to use Flash. This is FF 3 Beta 5, but happens on FF2 aswell on 8.04. Thanks!

---

### Post by psyke83 on 2008-04-24
It sounds like you're not using Adobe Flash, but the free implementation called swfdec.

```
$ sudo apt-get remove swfdec-mozilla
$ sudo apt-get install flashplugin-nonfree
```

The commands above should remove swfdec and install Adobe Flash that do not have this "play" button.

---

### Post by The Cake is a Lie on 2008-04-25
Hi psyke83, 

I removed swfdec and tried the second command. It says that the newest version is already installed. When I go on YouTube now, it says I do not have Flash and need to install it. Any help?

---

### Post by vsritual on 2008-04-26
Just install the latest version.  A new window will come up giving you a few options... I just installed the Adobe version now everything works fine!

---

