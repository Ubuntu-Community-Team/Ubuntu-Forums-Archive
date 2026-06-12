---
title: "restore points"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Matt26 on 2008-06-12
is there any type of automatic restore points that are created in ubuntu (8.04)?  something that would allow me to roll back my system setup to a few days ago?  thanks.

---

### Post by dondad on 2008-06-12
> **Matt26 said:**
> is there any type of automatic restore points that are created in ubuntu (8.04)?  something that would allow me to roll back my system setup to a few days ago?  thanks.

If you are looking for something analogous to system restore in Windows, then no.

---

### Post by cdtech on 2008-06-12
Just set up a good backup routine...

---

### Post by sdennie on 2008-06-12
Alternatively, if you are looking for restore points because you are going to be doing things that may cause problems to your system for experimentation purposes, you may want to look into virtualization technology (VirtualBox, VMWare, etc).  You can setup snapshots in a VM, completely destroy the VM and roll it back to your snapshot in a matter with seconds with no harm to your host machine.

---

### Post by wolfen69 on 2008-06-12
i find that keeping all my data on seperate drives/partitions makes the most sense. that way i can just re-install if need be. yes, it may be somewhat of a pain to set up your computer the way it was, but at least im assured of having a fresh system. i dont keep anything in /home, so it's no big deal. anything worth saving automatically gets saved to another drive. but that's just me.

but thankfully, [-o< i havnt had to anything to my machine since hardy came out. it just works.

---

### Post by hyper_ch on 2008-06-13
Backup.... make regurarly backups... even if you don't do anything, your harddisk can crash any day anyway... so: MAKE BACKUPS.

---

### Post by rraj.be on 2008-06-13
Yo can use partimage to clone your hard disk.

So you can restore the particular partition with that back up in minuits.

Advantages of partimage are.

Its faster.

It backs up only used memory.

You can even clone installed other os partition's.

Just you can get more info here.

```
[http://pittman.ws/articles/howto/partimage.html]("http://pittman.ws/articles/howto/partimage.html")
```

---

