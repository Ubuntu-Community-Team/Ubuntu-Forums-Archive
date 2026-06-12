---
title: "Website Building"
date: 2015-01-29
forum: Programming Talk
---

### Post by flaymond on 2015-01-29
Hello, I just wanna ask a few questions. I trying to make a website, and follow up some tutorial. It's fun at first, then when on PHP chapter...I frustated because I need a server to run it...I only have  a PC, can I use the same PC(that I use for writing here) to install the server and do my routines normally? For short -Can I install server in this PC to run PHP, and also use this PC to do programming, gaming, others in the same time?

---

### Post by Lars Noodén on 2015-01-29
You can install Nginx or Apache2 on your machine and it will not consume many resources unless it is active.  But if you like you can, in 1404 LTS, set them so that they have to be started and stopped manually using [update-rc.d](http://manpages.ubuntu.com/manpages/trusty/en/man8/update-rc.d.8.html).  

```

sudo update-rc.d apache2 disable S 2 3 4 5 

```

It will probably be slower on machines without much RAM due to use of swap.  Of the two, Nginx uses fewer resources.  You can use [top](http://manpages.ubuntu.com/manpages/trusty/en/man1/top.1.html) or [ps](http://manpages.ubuntu.com/manpages/trusty/en/man1/ps.1.html) to see how much is actually being used.

Then with one of those you can run PHP.

---

### Post by SeijiSensei on 2015-01-29
Use the method described in [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP) to install "lamp-server^".  You'll have a complete implementation of Apache, PHP, and MySQL. Try creating a file called /var/www/html/info.php like this:
```
sudo echo '<?php phpinfo() ?>' > /var/www/html/info.php
```
Then test it out by pointing the machine's browser to [http://localhost/info.php](http://localhost/info.php).

---

### Post by flaymond on 2015-01-30
Thanks for the advice!!! :D

---

