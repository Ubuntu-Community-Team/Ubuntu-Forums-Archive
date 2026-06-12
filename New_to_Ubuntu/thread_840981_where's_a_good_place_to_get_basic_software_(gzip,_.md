---
title: "where's a good place to get basic software (gzip, etc)?"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by sonaural on 2008-06-25
having trouble setting up flash player, i suspect because the default flash apps need to be unzipped and i haven't set up a secomp program

---

### Post by iaculallad on 2008-06-25
> **sonaural said:**
> having trouble setting up flash player, i suspect because the default flash apps need to be unzipped and i haven't set up a secomp program

Try using gnash instead, its available in the repo.

```
sudo apt-get install gnash
```

BTW: gzip terminal command is pre-installed in Ubuntu.

---

### Post by tramir on 2008-06-25
You can install applications via Synaptic (System - Administration - Synaptic Package Manager). If you can't find something there, you might check GetDeb, they have packages that are not always in the repositories. But from your question both flash and archivers are in the repositories. You can install flashplugin-nonfree and gzip either from a terminal, like was suggested before, or in Synaptic.

---

