---
title: "Gnome Version ??? which is correct?"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by cwmoser on 2012-08-22
From the command prompt:
$  gnome-session  --version 
gnome-session 3.2.1


But, via System Monitor -> System it displays:
GNOME 3.4.2


So which is correct?
My OS is Ubuntu 12.04 64-bit.

Can I access a Gnome menu directly???

Carl

---

### Post by Lisiano on 2012-08-22
I'd say whatever System Monitor says is correct, because
```
lisiano@Lisiano-Ubuntu:~$ gnome-calculator -v
gnome-calculator 6.4.1.1
``` when you ask it's version, it will only tell the apps version. You just might have an old session manager but gnome itself might be newer.

---

