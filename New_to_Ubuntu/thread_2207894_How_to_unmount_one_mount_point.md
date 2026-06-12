---
title: "How to unmount one mount point"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by BoneyOne on 2014-02-25
I accidentally caused a loop when setting up some of my mounts. I need to remove the one mount but keep all others.

```

/var/www/html/testbed/wp-content/plugins on /var/www/html/lubbock-tx/wp-content/plugins type none (rw,bind)
/var/www/html/testbed/wp-content/plugins on /var/www/html/state-nc/wp-content/plugins type none (rw,bind)
/var/www/html/testbed/wp-content/plugins on /var/www/html/desoto-fl/wp-content/plugins type none (rw,bind)
[COLOR=#ff0000]/var/www/html/testbed/wp-content/themes on /var/www/html/testbed/wp-content/themes type none (rw,bind) <-- remove this one only[/COLOR]

```

---

### Post by Habitual on 2014-02-25
```
sudo umount [COLOR=#ff0000]/var/www/html/testbed/wp-content/themes[/COLOR]
```?

---

