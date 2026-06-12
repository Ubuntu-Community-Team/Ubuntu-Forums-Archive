---
title: "Trying to get php to work!"
date: 2008-08-17
forum: Programming Talk
---

### Post by nilsh on 2008-08-17
Hi! 

I've installed apache2 and php5 on my Ubuntu 8.04 now, but can't get it to work.

I've made a folder inside var/www with a file called phpinfo.php inside of it.

The file contains <?php phpinfo() ?>.

Thing is, when I doubleclick it, and make firefox open it, it asks me to save or open the file. It doesnt show anything! Why is this?

Thanks in advance

nilsh

---

### Post by Kadrus on 2008-08-17
type into your browser: [http://localhost/](http://localhost/)
and you will see your files listed...click from there phpinfo.php and you will be able to see the webpage.

---

### Post by mike_g on 2008-08-17
You might ot have the apache2 service running; you could try restart it. I forgot the command but IIRC if you type apache2 --help it shoudl tell you.

>_< oh yeah, you will have to get to it via your webbrowser from localhost.

---

### Post by Kadrus on 2008-08-17
> **mike_g said:**
> You might ot have the apache2 service running; you could try restart it. I forgot the command but IIRC if you type apache2 --help it shoudl tell you.

```
sudo /etc/init.d/apache2 restart
```

---

### Post by jinksys on 2008-08-17
> **nilsh said:**
> Hi! 

I've installed apache2 and php5 on my Ubuntu 8.04 now, but can't get it to work.

I've made a folder inside var/www with a file called phpinfo.php inside of it.

The file contains <?php phpinfo() ?>.

Thing is, when I doubleclick it, and make firefox open it, it asks me to save or open the file. It doesnt show anything! Why is this?

Thanks in advance

nilsh

If you double click it, you are bypassing your server completely and the php file is not being interpreted. You need to type in your server's URL plus the path to the file, ie) [http://localhost/mypage.php](http://localhost/mypage.php)

---

### Post by suprfish on 2008-08-17
Installing php5 doesn't automatically enable the apache module (though it used to).

```
~$ sudo a2enmod php5
~$ sudo /etc/init.d/apache2 restart
```

---

### Post by nilsh on 2008-08-18
Thanks, that did the trick :D

---

