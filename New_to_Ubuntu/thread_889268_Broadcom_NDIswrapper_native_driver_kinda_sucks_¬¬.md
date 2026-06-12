---
title: "Broadcom NDIswrapper?? native driver kinda sucks ¬¬"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by holasoyneto on 2008-08-13
Dell Inspiron 1501, Ubuntu Hardy, AMD Sempron 3500+ and a gig of ram.

So, i have this laptop i use for school, it had vista on it, it all was fine since i only used firefox and openoffice, and suddenly my vista install died, and i had no license nor disc, so i installed ubuntu, cause im kinda familiar with it on my desktop, enverything is fine ati drivers sound just wireless so i installed the restrivted driver but it kinda sucked, it would detect the networks and conect to them but it would disconect in 30 seconds or so, so i wanted some help on this, since i went through lots of tutorials and nothing worked.
Thank You:)

---

### Post by falcon61102 on 2008-08-13
Could you open the terminal, run and post the results of:
```
lshw -C network
```
and
```
lspci
```

That will give us a better idea of what type of hardware you have.

---

