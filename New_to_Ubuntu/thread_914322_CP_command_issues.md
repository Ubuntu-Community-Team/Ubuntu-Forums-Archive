---
title: "CP command issues"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Tux.Ice on 2008-09-08
ok trying to do a backup with my commands -

```
venture@vserv$ cp -u /home/venture/Margaret /backup/Margaret
cp: Omitting Directory /home/venture/Margaret
```
WHat am i doing wrong?

---

### Post by sisco311 on 2008-09-08
use the -r flag to copy directories(recursively):```

cp -ru ...
```

---

### Post by t0p on 2008-09-08
> **Tux.Ice said:**
> ok trying to do a backup with my commands -

```
venture@vserv$ cp -u /home/venture/Margaret /backup/Margaret
cp: Omitting Directory /home/venture/Margaret
```
WHat am i doing wrong?

You need to use the **-r** flag to make the command recursive:

```
cp -u -r /home/venture/Margaret /backup/Margaret
```

Also, are you aware this command will create a directory called /backup - ie it will not be in your home directory but will stem from the / directory.

If you want the backup directory to be in your home directory, you should change the 2nd part of the command to 
```
~/backup
```

---

### Post by Tux.Ice on 2008-09-08
yes i am aware
and thnx ill try tommorow

---

