---
title: "[SOLVED] I think my php5 isn't working."
date: 2008-11-12
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-12
I created a test.php file.

<?php phpinfo(); ?>

I put it in my /var/www/

when i go to localhost/test.php it wants me to download test.php

Where do I start to figure out what is wrong with my php5 an how to fix it.

---

### Post by beercz on 2008-11-12
> **shanep-server said:**
> I created a test.php file.

<?php phpinfo(); ?>

I put it in my /var/www/

when i go to localhost/test.php it wants me to download test.php

Where do I start to figure out what is wrong with my php5 an how to fix it.
Do you have apache installed and configured correctly?

---

### Post by rustutzman on 2008-11-12
Find your php logs and have a look there. Look in the php install directory.

Russ

---

### Post by shanep-server on 2008-11-12
yes apache is working and so is mysql. I can view /var/www/index.html and i can create databases with mysql and add too them.

I'm checking phplog here in a second

---

### Post by shanep-server on 2008-11-12
where do u think the install directory is? Im not finding phplog

I looked in /etc/php5 but there is only 2 files apache2 folder and conf.d

php.ini is located in /etc/php5/apache2/

---

### Post by shanep-server on 2008-11-12
i got it. Lamp never installed php5 when i ran it. Weird how that works out since I installed Lamp server from synaptic packaged manager LOL. Oh well problem solved.

---

