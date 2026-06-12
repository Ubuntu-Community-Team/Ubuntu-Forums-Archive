---
title: "Does Apache affect anything if nothing uses it?"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by TehSofaWolf on 2011-09-27
I install Apache2 for rTorrent, but since then, I uninstalled rTorrent, and am reluctant to touch the Apache directory. Will it use resources if it remains unused?

---

### Post by dwasifar on 2011-09-27
> **TehSofaWolf said:**
> I install Apache2 for rTorrent, but since then, I uninstalled rTorrent, and am reluctant to touch the Apache directory. Will it use resources if it remains unused?

Chances are it's being started at boot, so yes, it will use resources.  

Do this:

```
sudo chmod -x /etc/init.d/apache2
```

...to stop it from loading on boot.

---

### Post by wildmanne39 on 2011-09-27
Hi, if it runs at startup it will use a little memory, also you want to make sure you set it up to be secure when you installed it.
Thank you

---

### Post by TehSofaWolf on 2011-09-27
Alrighty, thanks for the answers!

---

