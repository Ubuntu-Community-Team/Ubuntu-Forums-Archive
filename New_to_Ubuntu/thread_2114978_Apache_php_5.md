---
title: "Apache php 5"
date: 2013-02-11
forum: New to Ubuntu
---

### Post by heldemanpieter on 2013-02-11
i am very new to this. I installed Apache  php 5. In /var/www, i must create a text file called "test.php", and  grant the world (or, at least, Ubuntu user "apache") permission to read  it. In Terminal i now have to type "sudo ....?" and something to create a  file "test.php". In /var/www i have created a file index.html. How do i  create "test.php" in var/www and grant permission.Thank you. heldeman

 [EMAIL="heldemanpieter@gmail.com"]heldemanpieter@gmail.com[/EMAIL]

---

### Post by omeomi on 2013-02-11
First of all it is not a very good idea to post your emailaddress here (everyone can read it).

Second, if I understand what you want to do then these commands will do the trick:
```
$ sudo echo "<?php phpinfo(); ?>" >> /var/www/test.php
$ sudo chmod 644 /var/www/test.php
```

I added the content (phpinfo(); ) so the file does something but you can put something else in there of course

---

### Post by SeijiSensei on 2013-02-11
> **omeomi said:**
> First of all it is not a very good idea to post your emailaddress here (everyone can read it).

More importantly, it will be "harvested" by spammers and added to their lists.  Once an address appears on a website, the amount of spam that address receives quickly skyrockets.

By the way, the pseudo-user that Apache runs as in Ubuntu is called "www-data" not "apache".  That's the username used on RedHat and its clones like CentOS.

---

