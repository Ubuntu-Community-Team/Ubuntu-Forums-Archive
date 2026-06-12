---
title: "[SOLVED] finding source code"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by boblemur on 2008-09-15
i know this is probably something really obvious but where can i find source code for the programs that i have installed?? ie for apt-get (the source for that) or for gnome, or any of the programs installed in ubuntu by default.

thanks for any help in advance.

---

### Post by Dr Small on 2008-09-15
You can run:
```
sudo apt-get source *appname*
```

Or, you can browse the Debian / Ubuntu repository for the source of the application:
[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Dr Small

---

### Post by boblemur on 2008-09-15
thank you :) just wat i was looking for

---

### Post by jemate18 on 2008-09-15
> **boblemur said:**
> thank you :) just wat i was looking for

Please mark this thread as SOLVED

---

### Post by luridsorcerer on 2008-09-18
This works great! I've been wanting to know this for some time. However if you use ```
sudo apt-get source *appname*
``` root will own all the downloaded files. If you plan on changing them, it would probably be best to just leave the sudo out.  ```
apt-get source *appname*
``` This way you can edit and compile the files more easily because you will own them instead of root.

---

### Post by boblemur on 2008-09-19
lol yeh i found that out after grabbing a few packages and getting annoyed.

---

