---
title: "Cannot load mcrypt extension. Please check your PHP configuration."
date: 2008-05-16
forum: Programming Talk
---

### Post by figo2476 on 2008-05-16
After install phpmyadmin in kubuntu hardy, I found this message.

Doing sudo apt-get install php5-mcrypt doesn't help, as it says it is the latest installation. Any hint?

---

### Post by supirman on 2008-05-17
Did you try restarting apache?

Also, make a web page with <?php phpinfo(); ?> and look at the output to see if mcrypt is listed.

---

### Post by figo2476 on 2008-05-17
solved, by reinstall phpmyadmin + apache2

---

### Post by pe7er on 2008-10-08
> **figo2476 said:**
> Doing sudo apt-get install php5-mcrypt doesn't help

I installed phpmyadmin 3.0.0 manually and got the same error...
Thanks to the info in your post I was able to solve it with: 
```
sudo apt-get install php5-mcrypt
sudo /etc/init.d/apache2 restart
```

Thanks!

---

### Post by zenlenin on 2012-11-04
> **pe7er said:**
> sudo apt-get install php5-mcrypt
gets this error

E: Unable to locate package php5-mcrypt

---

### Post by AlexDudko on 2012-11-04
If it's hardy then there are no active repositories because this distribution has reached it's EOL (end of life) long ago.

---

