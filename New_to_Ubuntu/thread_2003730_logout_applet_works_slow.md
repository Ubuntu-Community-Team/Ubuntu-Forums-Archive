---
title: "logout applet works slow"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by lenypl on 2012-06-14
i upgrde 11.10 to 12.04 . now my logout applet dont work properly.when i select for shutdown or restart it response very slowly. but threw power switch i get a faster shut down

---

### Post by daslinkard on 2012-06-17
Have you tried utilizing the command line to shutdown such as:

```
sudo apt-get shutdown -h now
```

How quickly does this respond?

---

### Post by lenypl on 2012-06-18
when i try this command it shows like the attachment. and it doesnt shut down

---

### Post by Kakers on 2012-06-18
Remove the apt-get. :)

```
sudo shutdown -h now
```

---

### Post by lenypl on 2012-06-19
by command its work very fast.but its uncomfortable for  shut down always. thats why i am using log out applet in dock.can i get the same effect threw applet

---

### Post by Kakers on 2012-06-19
I'm assume you've done the upgrade option rather than a fresh install?

In my experience with Ubuntu, I don't go ahead with an upgrade as it always seems to cause problems for me. If you want a fast solution, an option may be to backup your data and do a fresh install of 12.04

---

### Post by lenypl on 2012-06-20
> **Kakers said:**
> I'm assume you've done the upgrade option rather than a fresh install?

In my experience with Ubuntu, I don't go ahead with an upgrade as it always seems to cause problems for me. If you want a fast solution, an option may be to backup your data and do a fresh install of 12.04
you are right. i made  an upgrade option. can you tell how can do a fresh install without losing data. i also have windows7 as dual boot

---

