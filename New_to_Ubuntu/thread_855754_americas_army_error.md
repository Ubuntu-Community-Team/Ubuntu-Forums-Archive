---
title: "americas army error"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by shayvasa on 2008-07-10
hi,
i installed americas army in ubuntu just like it says in the how-to but when i try to run it i get this error:
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
what can i do?

---

### Post by ChameleonDave on 2008-07-10
> **shayvasa said:**
> hi,
i installed americas army in ubuntu just like it says in the how-to but when i try to run it i get this error:
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
what can i do?

Looks like a dependency problem.  Perhaps you could install the missing software library and try again:

```

sudo apt-get install libstdc++5

```

---

### Post by shayvasa on 2008-07-10
it worked thanx, do u have any idea how can i make a shortcut on my desktop for this?

---

### Post by shayvasa on 2008-07-10
i have another problem now, it wont update punkbuster so i need to do it manually but i cant find it. any idea how to do this?

---

### Post by shayvasa on 2008-07-11
any1 plz?

---

