---
title: "[SOLVED] Lost in filesystem"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by kender42 on 2008-07-25
I want to add a program to my startup but I don't know where they are located. The program I want to add is Pidgin. I do know to go System->Preferences->Sessions but I just don't know where the programs are located. They aren't clearly marked like in the winblows os.

---

### Post by damis648 on 2008-07-25
You do not need to know the location. For the command in the sessions dialog, just simply type
```
pidgin
```
and that is all.

---

### Post by jordanmthomas on 2008-07-25
As the command, just put "pidgin"
Generally, most programs you run as a user are in /usr/bin.

For more information about how the filesystem is laid out:
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by drs305 on 2008-07-25
One note about pidgin that has generated some questions. When you first start it either with the command or via menu, it sometimes takes a minute or two for it to start and appear on the panel (if you have that option enabled). In any case, there have been a few posts from users who thought pidgin wasn't working when in fact they just needed to give it some time to establish its connection.

On my system, pidgin is listed in the Internet section of the menu.

---

### Post by kender42 on 2008-07-25
Thank you everyone. All of your information has helped. That solved this issue.

---

### Post by hogwartsnigel on 2008-07-25
Kender can you please mark this as solved..thanks

Nigel

---

### Post by tagra123 on 2008-07-25
If you want to know the full path to a binary the command is which


```
which pidgin
```

the output of the command is

/usr/bin/pidgin

---

