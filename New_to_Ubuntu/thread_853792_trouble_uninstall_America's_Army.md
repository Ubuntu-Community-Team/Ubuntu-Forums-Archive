---
title: "trouble uninstall America's Army"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by adobrakic on 2008-07-08
i've tried:

```

sudo sh /usr/local/games/armyops/uninstall

``` 

but i get:

"Could not find a usable uninstall program. Aborting."

i also tried "su root" but i get an "Authentication Error" 

any help?

---

### Post by tjwoosta on 2008-07-08
we could probably help you, but we would need to know how you installed it in the first place

(for instance was it a .bin or .run or .tar.gz or .deb)

---

### Post by adobrakic on 2008-07-08
oh, sorry. the installation was a .run

---

### Post by tjwoosta on 2008-07-09
```
cd /usr/local/games/armyops
```

then 

```
sudo ./uninstall
```

---

### Post by adobrakic on 2008-07-09
I just get:

```

Could not find a usable uninstall program. Aborting.
ado@ado-desktop:/usr/local/games/armyops$ 

```

again.

---

