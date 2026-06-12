---
title: "restoring logon menu"
date: 2015-10-27
forum: New to Ubuntu
---

### Post by rburkartjo on 2015-10-27
my wife is disabled so set up ubuntu 15.10 so it auto loads with no password. tried adding mate and messed system up. need to be able to get logon screen back and can fix from there/tks

---

### Post by rburkartjo on 2015-10-27
or terminal command to reinstall unity and force it to load as default.

---

### Post by Vladlenin5000 on 2015-10-27
Try:

```
sudo dpkg --reconfigure lightdm
```
selecting lightdm in the next dialog.

---

### Post by rburkartjo on 2015-10-27
vlad tks that did the trick

---

### Post by Vladlenin5000 on 2015-10-27
You're welcome. :-)

As usual, please mark this one as solved using the thread tools so future forum users may benefit as well.

---

