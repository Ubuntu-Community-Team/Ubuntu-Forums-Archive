---
title: "[SOLVED] custom start up sound?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by hvac3901 on 2008-06-25
Why can't i place sounds bites into /usr/share/sounds

so i can have my own start up sound, should i use sudo command in terminal?

edit more info: it says i do not have permission. :(

---

### Post by Eisenwinter on 2008-06-25
You need to be root to write the root file system ;)

/usr is located within the root file system.

Open your terminal, type su, give your root password.

After this, go to where the custom sound you want to move is located, with the cd command.

then:
```
mv ./<filename> /usr/share/sounds/
```
This will move it into the sounds directory.

Note you don't have to su, you can do this also with sudo, some prefer that.

---

### Post by hvac3901 on 2008-06-25
Thanks appreciated.

---

### Post by JoshuaRL on 2008-06-25
Another option is to open Nautilus (the file manager for Ubuntu) with root priviledges:
```

gksu nautilus

```
Be careful with that one, you can hurt your system.  If you use Kubuntu, Dolphin lets you open single folders as root, letting you do what you want.  Pretty cool.

---

### Post by hvac3901 on 2008-06-25
> **JoshuaRL said:**
> Another option is to open Nautilus (the file manager for Ubuntu) with root priviledges:
```

gksu nautilus

```
Be careful with that one, you can hurt your system.  If you use Kubuntu, Dolphin lets you open single folders as root, letting you do what you want.  Pretty cool.

EEEEWWWWWWW, Root power, with GUI....i love it. thanks.

---

