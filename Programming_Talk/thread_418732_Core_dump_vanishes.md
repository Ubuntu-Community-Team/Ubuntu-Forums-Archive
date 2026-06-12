---
title: "Core dump vanishes"
date: 2007-04-22
forum: Programming Talk
---

### Post by jonface on 2007-04-22
Whenever a C program dumps the core for whatever reason, it seems to get deleted. At first I thought it wasn't doing it but if I did:

"watch -n 0.2 myProg" and in another terminal "watch -n 0.2 cp core core.bak" I might just catch it in time.

I googled around but only found people who never get the core dump, not people who get it but it gets deleted.

Any ideas?

Ta.

2.6.17-11-generic
gcc (GCC) 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

---

### Post by amo-ej1 on 2007-04-23
have you enabled core dump ?

```

ulimit -c 900000

```

this sets the maximum size of a core dump to 900000, by default this is disabled ;)

---

### Post by jonface on 2007-04-23
I'm such a muppet, spelt it wrong the first time I tried it, 'unlimit' . Thanks!!

---

