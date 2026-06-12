---
title: "[SOLVED] Ubuntu isn't logging on... again. &amp;gt;.&amp;lt;"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by CJ Master on 2008-10-24
Well I had this same problem before, I tried to log in, but It wouldn't let me.

Last time I fixed this by logging into failsafe mode, and then running update manager.

But now, whenever I try to login, it'll show my desktop but nothing on it.

If it helps I just clean re-installed ubuntu and I have a 64-bit AMD.

Please help, I don't like failsafe terminal. :lolflag:

[hr]

EDIT: Seems I solved it, if your having a simular problem, try this.

First, log into failsafe terminal.

In terminal if you know root password its recomended to type **su** so you won't have to use the sumo command, but it works either way,

Now type in:
```
sudo apt-get update
```
Then:
```
sudo apt-get dist-install
```
After its finished then:
```
sudo update-manager
```

Hope it works!! :D

---

### Post by beno1990 on 2008-10-24
Can you give us some more details, such as what errors or problems occur when you try to log on?

---

### Post by CJ Master on 2008-10-24
No errors really, just a screen with my wallpaper on it. I just Ctr+Alt+Backspace out of it.

---

### Post by CJ Master on 2008-10-24
Oh I forgot, on my previous installation I installed via wubi, but not this time.

---

### Post by CJ Master on 2008-10-24
Alright I clean installed again, this time with 32-bit ubuntu, but still no dice.

...Well at least now it's only failsafe GNOME that only shows the the background, and normal gnome's the one that sends me automatically back to the login screen. -.-

---

