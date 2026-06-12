---
title: "setting shell for f8-f12"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by jcheung94 on 2012-09-04
could anyone explain to me how i could set shells to f8-12 (that open with crtl alt f8-12) please? :popcorn:

---

### Post by dodo3773 on 2012-09-04
> **jcheung94 said:**
> could anyone explain to me how i could set shells to f8-12 (that open with crtl alt f8-12) please? :popcorn:

Does Ubuntu use "/etc/inittab"? Probably what you are looking for.

---

### Post by sisco311 on 2012-09-04
Nope. Ubuntu uses Upstart.

@OP: You have to create an Upstart job in /etc/init

Something like:
**/etc/init/tty8.conf**
```
# tty8 - getty
#
# This service maintains a getty on tty8 from the point the system is
# started until it is shut down again.

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /sbin/getty -8 38400 tty8

```

---

### Post by Frogs Hair on 2012-09-04
The links might point you in the right direction.

[http://askubuntu.com/questions/77982/how-to-config-hotkeys-for-switching-between-consoles-in-ubuntu](http://askubuntu.com/questions/77982/how-to-config-hotkeys-for-switching-between-consoles-in-ubuntu)

[http://askubuntu.com/questions/147128/change-default-tty-shortcut](http://askubuntu.com/questions/147128/change-default-tty-shortcut)

---

### Post by sisco311 on 2012-09-04
On a second thought, you may want to check out some [terminal multiplexers]("http://en.wikipedia.org/wiki/Terminal_multiplexer") like GNU screen, tmux or dvtm+dtach.

[http://www.howtogeek.com/111417/how-to-multitask-in-the-linux-terminal-3-ways-to-use-multiple-shells-at-once/](http://www.howtogeek.com/111417/how-to-multitask-in-the-linux-terminal-3-ways-to-use-multiple-shells-at-once/)
[http://www.howtogeek.com/114582/2-alternatives-to-gnu-screen-for-linux-terminal-multitasking/](http://www.howtogeek.com/114582/2-alternatives-to-gnu-screen-for-linux-terminal-multitasking/)

---

