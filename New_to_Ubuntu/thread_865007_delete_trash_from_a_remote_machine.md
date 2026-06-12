---
title: "delete trash from a remote machine?"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by ginestre on 2008-07-20
Is it possible to delete trash via ssh?

---

### Post by scragar on 2008-07-20
Gutsy and earlier
```
rm ~/.Trash/*
```

Hardy and later(Ibex):
```
rm ~/.local/share/Trash/*
```

---

### Post by sujoy on 2008-07-20
> **ginestre said:**
> Is it possible to delete trash via ssh?

just ask yourself, why not? its just a directory. so basically if you have the correct permission then yes.

---

