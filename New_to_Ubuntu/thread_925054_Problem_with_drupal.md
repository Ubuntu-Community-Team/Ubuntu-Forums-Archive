---
title: "Problem with drupal"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by uppidada on 2008-09-20
C'd some one guide me in configuring and working on drupal...??
Firstly i'd like to say what i've done..
1.I've got a folder drupal-5.7 and copied it on to /etc/init.d/
2.Den i've gone thru /etc/init.d/drupal-5.7/drupal-5.7/sites/default(actually drupal-5.7 is present in another drupal-5.7 folder)
3.Well... later i've gone for chmod 777 settings.php
4.as i go thru my browser for [http://localhost/](http://localhost/)   ,m able to find only 1.apache2-default/  and 2.phpdemo/(which i use for PHP). sumone tell me about pblm and if possible all explanation of procedure and any other info that u find useful...

---

### Post by uppidada on 2008-09-20
Sumone help me with this....

---

### Post by leg on 2008-09-20
You don't need to put it in /etc at all. You have to put the contents of the folder in your web directory. This is [the guide]("http://drupal.org/getting-started/5") you need to read.

---

