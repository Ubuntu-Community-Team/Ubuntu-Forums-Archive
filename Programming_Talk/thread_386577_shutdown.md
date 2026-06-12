---
title: "shutdown"
date: 2007-03-17
forum: Programming Talk
---

### Post by lhabjane on 2007-03-17
Can I somehow shutdown from script without entering password?

I've heard that the easiest solution is to write a C-program and call some specific function?

---

### Post by tomchuk on 2007-03-17
Security concerns asside, the *easiest* solution is to make /sbin/shutdown suid root. A better solution would be to use sudo. You can allow certain users or groups to execute /sbin/shutdown with sudo without a password. Run visudo and enter something like:
```

%operator ALL= NOPASSWD: /sbin/shutdown

```
Now anyone in the opertator group can shutdown the machine without a password when using sudo.

---

### Post by lhabjane on 2007-03-17
This works as I wanted! THNX! :)

---

