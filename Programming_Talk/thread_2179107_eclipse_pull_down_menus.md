---
title: "eclipse pull down menus"
date: 2013-10-06
forum: Programming Talk
---

### Post by frankyboynl on 2013-10-06
hello, I installed eclipse and when I want to use one of the pull down menus like 'help', its not possible, none of the menus seem to open. I am currently using ubuntu 13.10


thanks in advance, Frank

---

### Post by Habitual on 2013-10-07
version....?
How did you pull down using the menus exactly? Mouse? Keyboard (Try Alt+H then A to see "About")
does it show?

---

### Post by Erik1984 on 2013-10-07
It appears to be a problem with Unity in 13.10:
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/1208019](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/1208019)

A workaround is mentioned in the following comment:
[https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/1208019/comments/8](https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/1208019/comments/8)

It suggest to run ecplipse in a modified environment and start it like this
```
env UBUNTU_MENUPROXY= eclipse
```

Can't test it out myself as I'm not using Unity. Subscribe to the bugreport if this bug affects you.

---

### Post by yournway on 2014-02-16
Hi Euroman,

Followed the first link to the bugs and modified the eclipse.desktop file as suggested, it worked.
I'm, however, hoping for a more elegant fix that has Eclipse working with unity like it should.

Many thanks for your help.

---

