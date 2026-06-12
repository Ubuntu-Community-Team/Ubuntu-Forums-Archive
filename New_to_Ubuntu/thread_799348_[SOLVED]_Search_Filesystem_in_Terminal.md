---
title: "[SOLVED] Search Filesystem in Terminal"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by anothrguitarist on 2008-05-18
Is there a way to search for a file using terminal?

---

### Post by wolfen69 on 2008-05-18
```
locate filename
```

---

### Post by Monicker on 2008-05-18
```
locate filename
```

If the file was recently added, you may need to do this first. 

```
sudo updatedb
```



You can also do 


```
find /dir -name filename
```


Which will search the dir and all subdirectories.  You can start at the root if you want.

```
find / -name filename
```

---

### Post by anothrguitarist on 2008-05-18
Thanks!

---

