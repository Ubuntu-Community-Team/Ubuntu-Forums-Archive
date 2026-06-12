---
title: "[SOLVED] No desktop"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by Nato99 on 2008-11-13
I just installed 8.10 and it worked just fine the first couple times but now it will only boot up into text mode. I seem to to have full access to all the directories and such, I just can't get it to switch over to Gnome or KDE. Any suggestions or do I need to reinstall? (I can still work off of the live disk just fine as well)

---

### Post by stephanvaningen on 2008-11-13
maybe some xorg.conf-issue? Have you been changing some configuration of display before this occured?

---

### Post by Sealbhach on 2008-11-13
Try

```
Xorg -configure
```

See here for further details:

[http://www.freebsd.org/doc/en/books/handbook/x-config.html](http://www.freebsd.org/doc/en/books/handbook/x-config.html)


.

---

### Post by mapes12 on 2008-11-13
If you can get to a console try:

```
sudo apt-get install ubunut-desktop
```

---

### Post by stephanvaningen on 2008-11-13
> **mapes12 said:**
> If you can get to a console try:

```
sudo apt-get install ubunut-desktop
```
typo:
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Nato99 on 2008-11-14
Okay, I tried "Xorg -configure" and got a fatal server error message stating "cannot move old file log blah blah blah"

Also tried the "sudo apt-get......" and nothing happened. However i tried it a second time just to be sure and it down loaded several files that appeared to be Gnome so i think we're in luck.

One real noob question - how do you start at GUI from the shell? I typed in "gnome" and got "command not found"

Thanks

---

### Post by REDace0 on 2008-11-14
It's 'gdm' for GNOME Desktop Manager, but you need 'sudo'.
```

sudo gdm

```

---

### Post by Nato99 on 2008-11-14
Thanks. GUI's back and all is right in the world again! :)

---

### Post by stephanvaningen on 2008-11-14
ok, please mark your thread as solved then (right-top 'Thread tools', ...)

---

