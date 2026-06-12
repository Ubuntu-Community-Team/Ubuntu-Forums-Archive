---
title: "Synaptic Package Manager Error"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-05
Hi all,
My Synaptic Package Manager can't open. It have a problem.
Here is the error.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Any idea ?

---

### Post by Rocket2DMn on 2008-05-05
Open a terminal and run
```
sudo dpkg --configure -a
```

---

### Post by Zeck on 2008-05-05
> **Rocket2DMn said:**
> Open a terminal and run
```
sudo dpkg --configure -a
```

Thanks very much.

---

