---
title: "Problem playing movies on Ext. DVD"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by Bill Reeves on 2013-02-08
I have a Dell Mini netbook with Ubuntu 11.10 OS installed.  When attaching the USB external DVD drive it will not play movies or anything on the DVD Player.  The software aps loaded when installing the OS will not work.  Any suggestions on how to fix the problem.

---

### Post by Kopkins on 2013-02-08
What do you mean it won't play? Does Ubuntu recognize that a disk was inserted? 

If they just won't play in the application (totem, vlc, etc.) try this: ```
 sudo /usr/share/doc/libdvdread4/install-css.sh
``` ****And make sure you have the restricted extras.```
sudo apt-get install ubuntu-restricted-extras
```

Best of luck, let us know how it works.

Kopkins

---

### Post by ACubed10 on 2013-02-08
yeah the suggestion above should help you out.  I had this problem as well when I first started with Ubuntu

---

### Post by Kopkins on 2013-02-08
> **ACubed10 said:**
> yeah the suggestion above should help you out.  I had this problem as well when I first started with Ubuntu

That's the only reason I know, ha. I had so much trouble figuring it.

---

