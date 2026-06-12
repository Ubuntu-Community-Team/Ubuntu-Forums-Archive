---
title: "Problem with sed -i command"
date: 2016-07-22
forum: New to Ubuntu
---

### Post by name2215 on 2016-07-22
Hello

what is the right command for:

```
sudo sed -i '/, false);/adefine( 'WP_MEMORY_LIMIT', '64M' );' /var/www/html/wp-config.php
```

 The result is ```
define( WP_MEMORY_LIMIT, 64M );
``` instead of ```
define( 'WP_MEMORY_LIMIT', '64M' );
```

Thank You

---

### Post by steeldriver on 2016-07-22
You can change the outer quotes from single to double, as explained here --> [http://unix.stackexchange.com/questions/297590/how-can-i-use-sed-to-append-a-line-with-qoutes-after-matching-pattern-found](http://unix.stackexchange.com/questions/297590/how-can-i-use-sed-to-append-a-line-with-qoutes-after-matching-pattern-found)

---

