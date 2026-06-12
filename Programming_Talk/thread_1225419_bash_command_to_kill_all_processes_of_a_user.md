---
title: "bash command to kill all processes of a user"
date: 2009-07-28
forum: Programming Talk
---

### Post by flylehe on 2009-07-28
Hi,
I like to kill all processes running on the server with my name as their "USER". Instead of providing their PIDs to kill individually, can I do it with simple way by specifying the USER?
Thanks and regards!

---

### Post by mali2297 on 2009-07-28
Try
```

pkill -U flylehe

```

---

### Post by Paul Miller on 2009-07-29
> **mali2297 said:**
> Try
```

pkill -U flylehe

```

I can't help but notice how Cthulhu-esque that command string looks. :P  (Appropriate, too, if it does what you're claiming -- I don't doubt it does, but I'm too lazy to look at the man page for pkill at the moment.)

---

