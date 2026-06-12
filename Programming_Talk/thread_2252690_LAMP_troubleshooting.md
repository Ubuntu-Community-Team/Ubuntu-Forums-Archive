---
title: "LAMP troubleshooting"
date: 2014-11-13
forum: Programming Talk
---

### Post by morninginfall on 2014-11-13
I've installed LAMP using 1 command (2 actually) like was written here [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) but, using NET Beans IDE 8.0.1 in PHP, created index.php (<?php phpinfo(); ?>) saved it in .\var\www\index.php Runned it as localhost\index.php .............. I get 


URL: [http://localhost/index.php](http://localhost/index.php)

**Not Found**

 The requested URL /index.php was not found on this server.
 [HR][/HR] Apache/2.4.7 (Ubuntu) Server at localhost Port 80


What the hell I'm doing wrong?

---

### Post by steeldriver on 2014-11-13
Hello and welcome to the forums

If you are running Ubuntu 14.04 then I believe the correct location should be 

```

/var/www/**html**/index.php

```

i.e. the default apache2 DocumentRoot is /var/www/html instead of just /var/www

---

### Post by morninginfall on 2014-11-13
> **steeldriver said:**
> Hello and welcome to the forums

If you are running Ubuntu 14.04 then I believe the correct location should be 

```

/var/www/**html**/index.php

```

i.e. the default apache2 DocumentRoot is /var/www/html instead of just /var/www

TY!! I should check  it in apache cfg!!!-)

---

