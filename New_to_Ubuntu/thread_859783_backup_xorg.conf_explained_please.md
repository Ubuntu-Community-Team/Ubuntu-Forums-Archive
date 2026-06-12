---
title: "backup xorg.conf explained please"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Sabar on 2008-07-14
I believe I have seen this posted a few times where some one is trying to help another budding Linux user how to fix a problem,

Be sure to backup xorg.conf. However as far as I can tell no one ever totally explains what it is. how it is used. and what it does.

Currently I am trying to fix a problem with going from a 17" monitor to a 32" wide screen HD T.V.  [[COLOR="Navy"]This is the post were I am trying to get help and I have some great answers just scared to try some of them yet[/COLOR]]("http://ubuntuforums.org/showthread.php?t=846774&highlight=Sabar")

Can some one vary carefully explain this line and how it is used to us newbies? I posted this question in the beginners are because we could use it the most I think.

Please remember to 
1. talk slowly
2. use small words ( that's mostly for me)
3. and please explain what it does, when you would use it, ( amusing it backs something up)how you save a point, and how you go back to that point.

Thank you I am sure more than just I will appreciate it.
Sabar

---

### Post by jimmy the saint on 2008-07-14
xorg.conf is the configuration file for you x-server.  the x-server is what enables your graphincal interface.  Without it, all you would see is text.  It is certainly more comlex than that, but to understand xorg.conf, that is what you need to know.  It is a text file that tells your x-server how to behave.  It determines how the graphical environment works.  You define your screen size, resolution, graphics driver, mouse behavior and various other aspects of the visual environment in which you operate.

In order to back it up, you simply make a copy of it with a name that you would recognize (xorg.conf.backup for example.)

a common way to do it in the command line would be:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

---

### Post by mevets on 2008-07-14
Backing up your xorg.conf is simply making a copy of the file when its in a working state (ie before you make any changes to it). This is useful because if you start making changes to it and you even up messing up things you can revert back. To back the file up run:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
To restore it:
```

sudo rm /etc/X11/xorg.conf && sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```

---

### Post by eriqjaffe on 2008-07-14
> **mevets said:**
> 
To restore it:
```

sudo rm /etc/X11/xorg.conf && sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf

```Actually,

```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```Works just as well.  ;)

---

