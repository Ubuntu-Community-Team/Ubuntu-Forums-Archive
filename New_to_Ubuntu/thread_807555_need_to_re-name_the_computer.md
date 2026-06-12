---
title: "need to re-name the computer"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-05-25
Running Ubuntu 8.04.  Need to change the name of the computer.  I gave it a specific name when I installed Ubuntu but I want to change it, as this is a dual boot machine and it will be much easier if it has the same name as XP (the other OS).

Any ideas?  I am clueless.

Thanks in advance,
Hank

---

### Post by nadjavox on 2008-05-25
You can change it under Network Settings -> Hostname

Go to System | Administration | Network and click on the General tab. You will see the host name listed there.

---

### Post by quelx on 2008-05-25
from the terminal

```
sudo nano -w /etc/hostname
```

Reboot

All done

---

