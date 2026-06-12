---
title: "Apache serving *.php.html* pages as php?"
date: 2010-04-15
forum: Programming Talk
---

### Post by somethingkindawierd on 2010-04-15
I have a web server running Apache that is serving *.php.html pages as php, not html.

Given the setup I'd prefer not editing the *.conf files for the virtual servers.

Does anyone know of a .htaccess trick to force Apache to server *.php.html files as html?

Thanks!

---

### Post by somethingkindawierd on 2010-05-19
bump

---

### Post by simeon87 on 2010-05-20
```
AddType text/html .php.html
```

---

