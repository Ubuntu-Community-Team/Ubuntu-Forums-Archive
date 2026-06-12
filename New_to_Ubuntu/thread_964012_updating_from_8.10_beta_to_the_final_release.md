---
title: "updating from 8.10 beta to the final release"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by migalhasm on 2008-10-30
How do I update from 8.10 beta to the final release?

Thanks

---

### Post by OrangeCrate on 2008-10-30
If you have applied all of the updates, you are now running the final.

---

### Post by kansasnoob on 2008-10-30
```
sudo apt-get update
```

```
sudo apt-get upgrade
```

And just to satisfy any unmet dependencies:

```
sudo apt-get -f install
```

If that last command gives you any prompts (like "auto-remove") just do what it says.

---

### Post by kansasnoob on 2008-10-30
> **OrangeCrate said:**
> If you have applied all of the updates, you are now running the final.

Yep!

---

### Post by migalhasm on 2008-10-30
ok thanks!

---

