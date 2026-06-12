---
title: "cant unistall wine???"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by malaya on 2008-05-10
- please help me im trying to uninstall wine but it diddt work...
- i received an error message after typing the commands

```

sudo apt-get remove wine
```

- here is the error message:

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

- please help me with this problem??

---

### Post by skymera on 2008-05-10
Do you have synaptic running?
Or any other things downloading such as updates etc?

---

### Post by DieB on 2008-05-10
This error appears when another apt process is running. Sure Synaptic or add/remove arent running?

If yes close them, or perform your action inside them.

+ remove leaves the setting files, while purge deletes them all


hope that helps

---

### Post by brettg on 2008-05-10
It can also happen when apt/synaptic are interrupted midstream.

If you are 100% sure nothing else is running do;

sudo rm /var/lib/dpkg/lock

to delete the lock file.

---

