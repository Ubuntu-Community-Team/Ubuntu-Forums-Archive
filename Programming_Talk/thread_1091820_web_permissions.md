---
title: "web permissions"
date: 2009-03-09
forum: Programming Talk
---

### Post by mcla0203 on 2009-03-09
what web permissions do you use?

i use:

```
chmod -R 755 root_web_dir
```

It is simple, quick for updates.

If there is stuff I don't want people to see or execute, I just put them in parent directory of web root.

---

### Post by Tibuda on 2009-03-09
It works if your host allows you to have files outsite the web root. If it does not, .htaccess comes to rescue.

---

