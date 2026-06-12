---
title: "[SOLVED] help, desktop totally transparent"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by poodpood on 2008-08-14
Newbie here!!!, I was messing around in Compiz Advanced Desktop Effect Setting on my other machine and put in a command in the General setting translucency box and now everything is translucent, like 100% invisible, apart from the desktop icons.

How can I manually disable compiz, bearing in mind I can't see the terminal window either.:confused:

---

### Post by LowSky on 2008-08-14
hot alt+F2

and type

```
metacity --replace
```

---

### Post by mick222 on 2008-08-14
I think maybe reboot and startup in recovery mode will allow you to repair compiz.

---

### Post by poodpood on 2008-08-14
> **LowSky said:**
> hot alt+F2

and type

```
metacity --replace
```

hot alt?

---

### Post by Troll_the_Great on 2008-08-14
I'm not sure, but you can try this: press Alt+F2 and type gnome-terminal (try hard to see where :D).After that click on the upper side of the desktop, and you should be in the terminal.Type
```
metacity --replace
```.I think this disables it.Good luck!
Cheers!

EDIT:Too slow...

---

### Post by poodpood on 2008-08-14
> **Troll_the_Great said:**
> I'm not sure, but you can try this: press Alt+F2 and type gnome-terminal (try hard to see where :D).After that click on the upper side of the desktop, and you should be in the terminal.Type
```
metacity --replace
```.I think this disables it.Good luck!
Cheers!

EDIT:Too slow...


It worked!!!! even though I had to type blindly!!!!

Thanks!!!!!

---

### Post by Troll_the_Great on 2008-08-14
Glad I could help.Please mark your thread as "Solved" using the "Thread Tools" from the top of your post.
Cheers!

---

