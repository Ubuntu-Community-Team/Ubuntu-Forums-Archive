---
title: "Configuring Apache"
date: 2007-03-05
forum: Programming Talk
---

### Post by mwero001 on 2007-03-05
Hi guys. I've been using wamp server for my web programming using php(in windows). I recently shifted to edubuntu and I still want to continue using apache. Any help please?

---

### Post by lnostdal on 2007-03-05
try:
```

sudo aptitude install apache2 php5
sudo /etc/init.d/apache2 restart

```

..then..

```

mkdir -p ~/public_html
echo "<?php echo 'hello world'; ?>" > ~/public_html/test.php
firefox http://localhost/~$USER/test.php

```

---

