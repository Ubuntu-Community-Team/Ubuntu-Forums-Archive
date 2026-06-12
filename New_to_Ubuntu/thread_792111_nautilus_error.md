---
title: "nautilus error"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Harisz750 on 2008-05-12
i just upgraded to ubuntu 8.04 and i have a problem with nautilus. when i run sudo nautilus. it opens it but also says:  (nautilus:6543): WARNING **: Unable to add monitor: Not supported...  what is this and how can i fix it??? i have to say that i unistalled the nautilus_share_extention cause it displayed an other error message about a share file

---

### Post by andrewski on 2008-06-11
Maybe you could move or rename ~/.gnome2/nautilus, which houses all your Nautilus settings? That'd most likely circumvent all problems. If so, you could just regenerate your settings from scratch, or maybe reintroduce the extensions one by one?

Also, does it work if you run `sudo -s; nautilus`? That elevates to root permissions first and *then* runs Nautilus. If that didn't work, I'd think it'd be a problem with Nautilus itself.

Hope this helps!

---

### Post by Najand on 2008-06-12
Use
```

gksu nautilus

```
instead of sudo command.

---

### Post by _sphinx_ on 2008-06-12
I also get the same warning message every time I do sudo nautilus but I dont' see any type of misfunctionality in nautilus and I just let it go. Cool solution. :P

---

### Post by andrewski on 2008-06-12
> **Najand said:**
> Use
```

gksu nautilus

```instead of sudo command.
Or install nautilus-gksu, which will give you an "Open as administrator" action on the Edit menu. Probably the best way to solve this, as well as offering you the chance to open files this way. :)

---

