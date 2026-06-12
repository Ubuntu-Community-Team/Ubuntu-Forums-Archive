---
title: "Php"
date: 2007-11-15
forum: Programming Talk
---

### Post by COLiNx86 on 2007-11-15
I'm learning PHP well i was until I moved to Linux. So my question is what do i need to start programming php in Ubuntu?

---

### Post by LaRoza on 2007-11-15
LAMPP
```

sudo tasksel

```

Select Lampp.

Your web directory is in /var/www.

If you are only going to be developing on this, and not actually serving public sites, you can ease the permission issues by making that directory yours. ```
chown $USER:$USER /var/www
```

---

