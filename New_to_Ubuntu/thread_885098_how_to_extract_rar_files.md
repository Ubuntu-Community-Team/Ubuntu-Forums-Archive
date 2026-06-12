---
title: "how to extract rar files"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-09
how can i extract rar files?

---

### Post by finer recliner on 2008-08-09
```
sudo apt-get install unrar
```

then right click your file and choose "extract"

---

### Post by InfinityCircuit on 2008-08-09
Remember that if you want to use unrar from the command line it has non-standard syntax:

whereas for a normal command like "rm" to add a modifier you would do "rm -r", for unrar you don't want the hyphen.  So it's:

```
unrar e file.rar
```

---

