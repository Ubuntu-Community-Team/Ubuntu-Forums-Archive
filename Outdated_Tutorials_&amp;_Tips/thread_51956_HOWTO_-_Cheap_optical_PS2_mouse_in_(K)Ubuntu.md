---
title: "HOWTO - Cheap optical PS2 mouse in (K)Ubuntu"
date: 2005-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by daigorobr on 2005-07-25
Recently I bought some cheap optical mouse for my computer (got tired of cleaning ball mouses) and noticed that it would jump and move completely unaccordingly to my movements.

Went there, came back and discovered that the solution is simpler than I expected.
Just change, in /etc/modules the line

```
psmouse 
```

for

```
psmouse proto=exps
```

Don't ask me what it does, but it works.

---

