---
title: "Buckups - duplicity files question"
date: 2022-05-03
forum: New to Ubuntu
---

### Post by jmichaels29 on 2022-05-03
After using backups to backup to my secondary HD, I noticed that many "duplicity" files exist now.

Curious as to why so?

screenshot attached - see 2nd screenshot

---

### Post by deadflowr on 2022-05-03
duplicity is the backend that the backup program deja-dup uses.
deja-dup is the default backup program that comes with Ubuntu.

---

### Post by jmichaels29 on 2022-05-03
It only started doing this after a clean install with latest LTS.  I'm sure it's nothing to worry about, considering what you typed.  It's just a little annoying that a bazillion duplicity files are created on my backup hd....

---

### Post by deadflowr on 2022-05-03
You can simply create a folder and move them into it.
Then if you want to restore later, just set the storage location to the created folder.

---

### Post by jmichaels29 on 2022-05-03
> **deadflowr said:**
> You can simply create a folder and move them into it.
Then if you want to restore later, just set the storage location to the created folder.

Thanks so much.
Marking as solved...

---

