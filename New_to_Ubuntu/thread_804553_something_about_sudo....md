---
title: "something about sudo...?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by lunaluna on 2008-05-23
when i start a "sudo" application through the graphical environment,i realize that for a while i can still do that with some other apps as weel..
how long does this last?

---

### Post by TeoBigusGeekus on 2008-05-23
About 15min I think.

---

### Post by BlackDragonBE on 2008-05-23
Or until you close the terminal session

---

### Post by lunaluna on 2008-05-23
> **BlackDragonBE said:**
> Or until you close the terminal session

i said graphical environment...

---

### Post by lunaluna on 2008-05-23
does this means also that other apps which don't need to be ran through sudo will with these priviledges?

---

### Post by Bodsda on 2008-05-23
no, if it does not need root privileges then it will not be given them, if you wish to reset the timer use 

```
 sudo -k 
```

all on its own and it will ask for a password again (usefull for writing nautilus bash scripts)

---

### Post by sayakb on 2008-05-23
For GUI apps, use gksudo.
If you once use sudo/gksudo with any GUI app, it would be recognized and you won't be furthur asked for password for about 15 minutes. But ofcourse, for the CLI, you might be asked for your password again.

---

