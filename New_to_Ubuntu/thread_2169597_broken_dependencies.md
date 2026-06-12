---
title: "broken dependencies"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by megabean on 2013-08-22
linux-headers-generic: Depends: linux-headers-3.5.0-39-generic but it is not installed
can anybody help me with this? first it was 3.5.0-37 and now it's 3.5.0-39.
:confused: need to upgrade but it won't let me, i'm using 12-10 now
thanks all.

---

### Post by ibjsb4 on 2013-08-22
To upgrade kernel in terminal:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

