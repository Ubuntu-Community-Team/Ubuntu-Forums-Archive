---
title: "cannot install .tar.bt2"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by alokme on 2008-10-11
i've a file ipwraw-ng.tar.bt2 placed on desktop
but when i type "tar xvjf package.tar.bz2" in terminal
it says file not found

i'm using ubuntu 7.04
pleasse help me

---

### Post by dhughes on 2008-10-11
I'd say you're just not in the correct place.

 Try ```
tar xvjf /home/[username]/Desktop/ipwraw-ng.tar.bz2
```  of course [username] is whatever name you use.

---

### Post by tjwoosta on 2008-10-11
you could use that, but instead of /home/username/ you could use ~/  
(its a shortcut)


so it would be like

```

tar xvjf ~/Desktop/ipwraw-ng.tar.bz2

```

---

