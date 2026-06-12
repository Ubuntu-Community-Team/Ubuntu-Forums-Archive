---
title: "another stupid question... for updates"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-12
since i have uninstalled  all games from my box why i get updates for them?

---

### Post by philinux on 2008-06-12
> **lunaluna said:**
> since i have uninstalled  all games from my box why i get updates for them?

Updates contain apps that you don't have installed too.

So you can install the latest version if you need.

---

### Post by Gannon8 on 2008-06-12
What specifically is updating?

Edit: Ok, what he ^ said

---

### Post by Najand on 2008-06-12
You probably have some orphan packages still remaining after removing games from your computer.
Remove them using this command:
```

sudo apt-get autoremove

```

---

### Post by kpkeerthi on 2008-06-12
> **lunaluna said:**
> since i have uninstalled  all games from my box why i get updates for them?

If you have uninstalled a package, your update notifier should not list an update for the package.

To completely uninstall all games, run this command in a terminal:
```
sudo apt-get purge gnome-games
sudo apt-get autoremove

```

---

### Post by philinux on 2008-06-12
> **Najand said:**
> You probably have some orphan packages still remaining after removing games from your computer.
Remove them using this command:
```

sudo apt-get autoremove

```

Just cos you remove the app they could still be in the repo if they were from the main repo's. So any updates ubuntu release will come through the normal update process.

---

### Post by rraj.be on 2008-06-12
In windows all softwares have their own libraries which make its .exe file.

So if even same library function is used by two diffrent programs each will have their own copy of its library files making the memory wasted.

But in ubuntu its shared pavkage system.

The packages are generally shared between all Programs.

even though you have uninstalled some games its package updates may be required by some other package and thus you are getting these thing's.

---

### Post by lunaluna on 2008-06-12
> **kpkeerthi said:**
> If you have uninstalled a package, your update notifier should not list an update for the package.

To completely uninstall all games, run this command in a terminal:
```
sudo apt-get purge gnome-games
sudo apt-get autoremove

```

tried it,some things were removed (about 225 mb) but i still have those 2 updates...:
   gnome-cards-data
   gnome-games-data    so...anything else to try?

---

### Post by kpkeerthi on 2008-06-12
Run ```
sudo apt-get update
``` to reload your update list.

---

### Post by lunaluna on 2008-06-12
> **kpkeerthi said:**
> Run ```
sudo apt-get update
``` to reload your update list.

done for 2nd time,i still have them...

---

### Post by kpkeerthi on 2008-06-12
Uninstall them.

```
sudo apt-get gnome-cards-data gnome-games-data
```

---

### Post by lunaluna on 2008-06-12
> **kpkeerthi said:**
> Uninstall them.

```
sudo apt-get gnome-cards-data gnome-games-data
```

you forgot the"remove"  :lolflag:
but it worked thanks

---

### Post by kpkeerthi on 2008-06-13
> **lunaluna said:**
> you forgot the"remove"  :lolflag:
but it worked thanks

LOL.. yes. Glad you got it.

---

