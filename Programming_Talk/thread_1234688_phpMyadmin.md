---
title: "phpMyadmin"
date: 2009-08-08
forum: Programming Talk
---

### Post by credobyte on 2009-08-08
Install it:
```
sudo apt-get install phpmyadmin

```

Open Apache config file:
```
sudo gedit /etc/apache2/apache2.conf
```

Add this line at the end of the file:
```
Include /etc/phpmyadmin/apache.conf
```

Restart Apache:
```
sudo /etc/init.d/apache2 restart
```

---

