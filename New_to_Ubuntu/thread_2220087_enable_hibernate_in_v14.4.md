---
title: "enable hibernate in v14.4"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by reza.bigham90 on 2014-04-26
hi
i using ubuntu 14.4
i cant enable hibernate!!!
i test below codes but they dont works?
```
sudo nano  /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
--> 
[Re-enable hibernate by default]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes
-OR-
-->
[Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

[Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate
ResultActive=yes


```

OR :
```


sudo pm-hibernate


```

---

### Post by trag on 2014-04-26
follow this link to setting up hibernation in 14.04   [http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/)
good luck
trag

---

