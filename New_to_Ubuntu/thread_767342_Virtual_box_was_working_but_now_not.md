---
title: "Virtual box was working but now not"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by NOLU on 2008-04-25
I only got the thing going last night but after the upgrade to 8.04, I get this error when opening XP up in the box.

[http://img512.imageshack.us/my.php?image=screenshotuc6.png](http://img512.imageshack.us/my.php?image=screenshotuc6.png)

I've gone into users and groups and nothing was changed in there. The only thing that is different is the upgrade.

Thanks.

---

### Post by Oldsoldier2003 on 2008-04-25
> **NOLU said:**
> I only got the thing going last night but after the upgrade to 8.04, I get this error when opening XP up in the box.

[http://img512.imageshack.us/my.php?image=screenshotuc6.png](http://img512.imageshack.us/my.php?image=screenshotuc6.png)

I've gone into users and groups and nothing was changed in there. The only thing that is different is the upgrade.

Thanks.

synaptic has the virtualbox ose modules. search for virtualbox

---

### Post by NOLU on 2008-04-25
There are quite a few there. Do I choose all of them?

---

### Post by Oldsoldier2003 on 2008-04-25
> **NOLU said:**
> There are quite a few there. Do I choose all of them?

chose the version that matches your kernel.
```

uname-r
``` will give you your kernel version

---

### Post by NOLU on 2008-04-25
Sorry but I'm getting command not found in terminal.

---

### Post by spiderbatdad on 2008-04-25
give a space after uname like:```
uname -r
```

---

### Post by NOLU on 2008-04-26
Got that and installed about 7 modules. Did a restart but now Ubuntu is very slow since doing that. I did open up virtualbox and got past the error message to the XP boor screen but it just got stuck and I had to turn the computer off and on.

It's very slow though.

---

