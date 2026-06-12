---
title: "apparmor dazuko incompatibility"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-25
Hi! I'm Melvin from India.
I installed AVG for linux workstation recently and compiled dazuko kernel module for real time file scanning in ubuntu 7.10.As root, i gave this code.
```

./configure 
make
make test
insmod dazuko.ko
make install
```

The error was that the module could not be inserted.
Then, i gave this code:

```

sudo rmmod apparmor
sudo insmod dazuko.ko

```
and the dazuko module works, but the apparmor module can't be reloaded.
How important is apparmor, what does it do and how to get it back working with dazuko?

---

### Post by RealPSL on 2008-07-26
The details on why apparmor is enabled are here [https://wiki.ubuntu.com/AppArmor?highlight=%28apparmor%29]("https://wiki.ubuntu.com/AppArmor?highlight=%28apparmor%29")

---

### Post by ice60 on 2008-07-26
i answered this in one of the three threads he's started asking about this, he was on the forum eariler and doesn't reply to his threads lol
[http://ubuntuforums.org/showthread.php?t=870090](http://ubuntuforums.org/showthread.php?t=870090)
[http://ubuntuforums.org/showthread.php?t=869069](http://ubuntuforums.org/showthread.php?t=869069)
[http://ubuntuforums.org/showthread.php?t=869056](http://ubuntuforums.org/showthread.php?t=869056)

---

