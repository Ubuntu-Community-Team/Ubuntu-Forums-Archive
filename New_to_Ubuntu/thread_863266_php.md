---
title: "php"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by sudeepk on 2008-07-18
I have installed php5 in my ubuntu with all the nesseary files. But when i open the site through my web brower it ask's me to save the file... can you help me out please.. i am using apache2

---

### Post by schwascore on 2008-07-18
See this post:

[http://ubuntuforums.org/showthread.php?t=167493](http://ubuntuforums.org/showthread.php?t=167493)

---

### Post by bobbocanfly on 2008-07-19
From the link:

Obviously apache isn't set up correctly to serve php pages. Uninstall everything php related in synaptic and follow [this guide]("http://easylinux.info/wiki/Ubuntu#How_to_install_PHP_for_Apache_HTTP_Server") to setting it up.

---

### Post by hyper_ch on 2008-07-19
```

sudo a2enmod php5

```

---

