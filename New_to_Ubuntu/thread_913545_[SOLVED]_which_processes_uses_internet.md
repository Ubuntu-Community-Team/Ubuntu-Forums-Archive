---
title: "[SOLVED] which processes uses internet"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by roquefilipe on 2008-09-07
I would like to know of a way to checkout which processes are using internet. Is it possible?

---

### Post by iaculallad on 2008-09-07
> **roquefilipe said:**
> I would like to know of a way to checkout which processes are using internet. Is it possible?

In your terminal:

```
netstat -ap | grep "LISTEN "
```

---

### Post by stroyan on 2008-09-07
> **iaculallad said:**
> In your terminal:

```
netstat -ap | grep "LISTEN "
```

You don't really want to use 'grep "LISTEN"'.
Connections in other states are certainly interesting as well.
The "ESTABLISHED" state is the most common one for active connections.

---

