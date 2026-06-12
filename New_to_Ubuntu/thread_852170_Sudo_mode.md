---
title: "Sudo mode"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by MONKEY4SALE on 2008-07-07
Hello all, When trying to do a command in sudo I get this error:sudo: /etc/sudoers is mode 0555, should be 0440

how do I fix this? It is really bothersome because thats all it tells me....

---

### Post by lazyart on 2008-07-07
Never saw that, but I guess```
sudo chmod 0440 /etc/sudoers
```would do the trick... but you can't do that either.

Boot into recovery mode (it's an option from grub) then type that in (without sudo), then reboot the system normally.

---

### Post by mali2297 on 2008-07-07
The command to change the mode is
```

chmod 0440 /etc/sudoers

```
However, you need to execute this as root. If sudo doesn't work, perhaps you can still boot in recovery mode and execute the command from there.

---

### Post by MONKEY4SALE on 2008-07-07
thanks

---

