---
title: "I was looking at website GZip compression and..."
date: 2010-09-05
forum: Programming Talk
---

### Post by James78 on 2010-09-05
This website feels a little slow at times, so I checked if this site was GZip compressed, and it's not! 100kb normal forum topic listing, and it could be compressed 80% to 20kb! Faster downloading for the users, and less bandwidth usage for the server! I was quite surprised when I found this...

Link for reference..
[http://www.gidnetwork.com/tools/gzip-test.php](http://www.gidnetwork.com/tools/gzip-test.php)

... And enter a URL to one of these pages.

---

### Post by Bachstelze on 2010-09-06
gzip compression would put additional load on the CPU. I don't think we need that right now.

---

### Post by James78 on 2010-09-06
> **Bachstelze said:**
> gzip compression would put additional load on the CPU. I don't think we need that right now.
I am aware of that, although **usually** the extra load is worthit for the bandwidth saved, and faster browsing for users. Either way, it depends on the server. Still though, it'd be much faster browsing huh? ;)

---

### Post by Bachstelze on 2010-09-06
> **James78 said:**
> I am aware of that, although **usually** the extra load is worthit for the bandwidth saved, and faster browsing for users.

Usually. Here, the CPU is already working close to full load. Add the load of gzipping millions of pages per day, and you bring it to its knees, meaning no browsing for anyone.

---

### Post by James78 on 2010-09-06
> **Bachstelze said:**
> Usually. Here, the CPU is already working close to full load. Add the load of gzipping millions of pages per day, and you bring it to its knees, meaning no browsing for anyone.
Haha ya.

---

### Post by worseisworser on 2010-09-06
Huh? This site is actually CPU-bound?

I don't know too much about PHP, but I recall there being some compiler/cache thing available for it?

---

### Post by Bachstelze on 2010-09-06
> **worseisworser said:**
> Huh? This site is actually CPU-bound?


The load average is constantly well above one.

---

