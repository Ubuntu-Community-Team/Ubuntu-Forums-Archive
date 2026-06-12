---
title: "PHP - Show server uptime on Windows box"
date: 2007-01-08
forum: Programming Talk
---

### Post by ironfistchamp on 2007-01-08
Hey all

Does anyone know how I can write a script to show the servers uptime? It is a windows box so any tutorials or scripts I have found don't work (*nix only).

Thanks

Ironfistchamp

---

### Post by Jussi Kukkonen on 2007-01-08
I don't know PHP, so you'll have to figure out the integration yourself, but I did have to find out about this a few years back (when I still had something to do with Windows)

On XP: 
```
Systeminfo | Find "Up Time"
```
This should work on older systems too, but it only gives you the start date:
```
net stats srv
```

---

### Post by enopepsoo on 2007-01-08
if you allowed the php script to execute, you could just call the uptime command.
```
uptime
```

---

### Post by patty522 on 2007-01-08
> **ironfistchamp said:**
> Hey all

Does anyone know how I can write a script to show the servers uptime? It is a windows box so any tutorials or scripts I have found don't work (*nix only).

Thanks

Ironfistchamp

its a server2003 if that makes any difference

---

### Post by ironfistchamp on 2007-01-08
Thanks for your help I shall give that a go.

---

