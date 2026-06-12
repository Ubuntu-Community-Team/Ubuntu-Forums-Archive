---
title: "[SOLVED] Sick Ibex"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by nnjond on 2008-11-26
Hi,  rare failure of my os.

Just rebooted where it passed a routine check, but probs persist:


My desktop icons have disappeared my wastebasket wont open and I think its time i emptied it, and generally running very slow. 

"nautilus can't be used at the moment due to an unexpected error"

---

### Post by bruce89 on 2008-11-26
Perhaps there is no disk space left.

```

rm -fr .local/share/Trash

```

This will forcably remove the Wastebasket (or whatever you want to call it).

Before doing that, paste the output of 
```

ls -lh .local/share/Trash

```

---

### Post by nnjond on 2008-11-26
nick@nick-desktop:~$ ls -lh .local/share/Trash
total 320K
drwx------ 2 nick nick 132K 2008-11-26 12:32 files
drwx------ 2 nick nick 180K 2008-11-26 12:32 info
nick@nick-desktop:~$

---

