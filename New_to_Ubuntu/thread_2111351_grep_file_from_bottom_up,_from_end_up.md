---
title: "grep file from bottom up, from end up"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by Kevin McCready on 2013-02-01
Does anyone know how to use grep to search for a string from the bottom of the file (not from the top).

Thanks

---

### Post by steeldriver on 2013-02-01
well it's ugly - but you could use 'tac'

```
tac *yourfile* | grep *expression*
```

---

### Post by Kevin McCready on 2013-02-01
cute. thanks. didn't know about taccy cat tac yccaty

---

