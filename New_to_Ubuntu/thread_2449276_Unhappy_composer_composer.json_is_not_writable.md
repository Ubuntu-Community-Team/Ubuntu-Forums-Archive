---
title: "Unhappy composer: composer.json is not writable"
date: 2020-08-24
forum: New to Ubuntu
---

### Post by oldiee on 2020-08-24
Hi there, I have Ubuntu/VPS, nginx, mariadb, /var/www/html/test.com/composer.json: permission=755, chown/chgrp=www-data/www-data


oldiee> composer update/upgrade
```
Update symfony/polyfill-ctype (v1.17.0 => v1.18.1) : Update failed (Could not delete /vendor/symfony/polyfill-ctype/README.md)


In Filesystem.php line 217:
Could not delete /vendor/symfony/polyfill-ctype/README.md
```

odiee> composer require symfony/polyfill-ctype
```

./composer.json is not writable.
```


Can you help me? I am almost newbie to this.

---

