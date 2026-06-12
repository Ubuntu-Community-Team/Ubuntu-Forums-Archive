---
title: "Cannot empty wastebasket in 8.04 64bit"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by Ubangi on 2008-06-02
I have some files stuck in there that won't go away.
Also, the system is very slow to shut down.

I cannot even find ~/.trash or anything like that to rm it.
Why is the basket getting stuck, and worse still, why is it hidden?

---

### Post by sayakb on 2008-06-02
At a terminal, issue:
```
sudo rm -rf ~/.local/share/Trash/files
```

---

### Post by adamogardner on 2008-06-02
you might need to upgrade to dumpster 2.0

---

