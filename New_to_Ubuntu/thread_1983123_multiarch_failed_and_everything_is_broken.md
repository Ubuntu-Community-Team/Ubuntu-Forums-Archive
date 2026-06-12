---
title: "multiarch failed and everything is broken"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by dayzman on 2012-05-19
Hi

I tried to enable multiarch with:

```
echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarchsudo 
apt-get install libxss1:i386 libqtcore4:i386 libqt4-dbus:i386
```

it removed kile, okular, and many other packages. But now I can't install them again. If I try

```
sudo apt-get install kile
```

I get

```
The following packages have unmet dependencies.
 kile : Depends: konsole but it is not going to be installed
        Depends: kde-runtime but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Any help will be appreciated.

Thanks

---

### Post by Lisiano on 2012-05-19
Hello. Multiarch is enabled by default in Ubuntu 12.04
I also notice you marked the thread as solved, yet you didn't post the solution. Please post your solution as it might help others.

---

### Post by dayzman on 2012-05-19
> **Lisiano said:**
> Hello. Multiarch is enabled by default in Ubuntu 12.04
I also notice you marked the thread as solved, yet you didn't post the solution. Please post your solution as it might help others.

I was going to, but it wasn't very clear to me either. I kept tracing each conflicting package and found the root. I called apt-get install manually for that conflict package and that seems to have fixed it.

Sorry for being vague.

---

