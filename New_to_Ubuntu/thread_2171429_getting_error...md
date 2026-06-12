---
title: "getting error.."
date: 2013-08-30
forum: New to Ubuntu
---

### Post by amit_samanta on 2013-08-30
how to solve it??

---

### Post by su:bhatta on 2013-08-30
This simply means that 'gnome-mount' is not  in the Ubuntu repsitories.

You have to either add a ppa which has gnome-mount or you can see if it it available through gnome.org 

Please excuse my ignorance, what is 'gnome-mount'?

---

### Post by ant2 on 2013-08-30
I think gnome-mount was replaced by udisks.

---

### Post by eternal243 on 2013-08-30
> **ant2 said:**
> I think gnome-mount was replaced by udisks.

correct, udisks is the new replacement.

use the following code to install it: 

```
sudo apt-get install udisks
```
[B]
edit:[/B] unless the OP is using an old version of Ubuntu where gnome-mount is supposed to be in the repository.
also, gnome-mount can still be installed if you install it manually from a deb package. =)

---

