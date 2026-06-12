---
title: "Fusion graphics not there at startup?"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Watchtow3r on 2008-07-06
All of a sudden, the compiz fusion graphics aren't there at startup. I can't use the cube and the windows don't wobble without me clicking on the fusion icon and clicking "reload window manager". How can I make it on by default again?

---

### Post by billgoldberg on 2008-07-06
> **Watchtow3r said:**
> All of a sudden, the compiz fusion graphics aren't there at startup. I can't use the cube and the windows don't wobble without me clicking on the fusion icon and clicking "reload window manager". How can I make it on by default again?

Go to "system -> preferences -> sessions" and add a new entry.

The command should be 

```
compiz --replace
```

if you use emerald, you'll need to make an entry for that to

```
emerald --replace
```

---

### Post by Watchtow3r on 2008-07-06
thanks!

---

