---
title: "[SOLVED] Trashcan shows empty aven though trash file is full."
date: 2008-07-21
forum: New to Ubuntu
---

### Post by alienexplorers on 2008-07-21
What do I do yo get my trash icon working.  Also when I click Empty Trash nothing happens.  I have to go in under root to delete the files.

---

### Post by Rolcol on 2008-07-21
You probably did something to the permissions or you were trying to delete files owned by root.  Maybe this will help:

```

sudo chown -R $USER ~/.local/share/Trash/

```

What that does is set you as the owner of the folders and files used to make up the trash.


Hopefully someone corrects me if I'm wrong.

---

### Post by Liakath on 2008-07-21
Dear alienexplorers,

> **alienexplorers said:**
> What do I do yo get my trash icon working.  Also when I click Empty Trash nothing happens.  I have to go in under root to delete the files.

You may try removing it from the panel and again adding it; see whether it works!

Liakath

---

### Post by alienexplorers on 2008-07-21
Already tried removing the panel icon and replaceing it after a restart.

---

### Post by Liakath on 2008-07-22
Dear alienexplorers,

> **alienexplorers said:**
> Already tried removing the panel icon and replaceing it after a restart.

The thread is marked as solved. Were you able to resolve it and if yes how? Kindly post how it was solved for benefit of others.

Liakath

---

