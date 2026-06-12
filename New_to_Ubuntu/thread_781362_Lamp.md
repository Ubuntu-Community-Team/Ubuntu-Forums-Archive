---
title: "Lamp"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by shoaibi on 2008-05-04
Can anyone guide me on how to install a LAMP server along with PHPMyAdmin and all that necessary stuff on Ubuntu?

I know about XAMPP, but i wanna install a pure LAMP by myself which would contain everything that XAMPP has....

---

### Post by GavinZac on 2008-05-04
install apache, php5, mysql and phpmyadmin, from the repositories. Thats how I did it.

---

### Post by bobbocanfly on 2008-05-04
```
sudo apt-get install apache2 php5 libapache2-mod-php5 php5-mysql mysql-server
```

Might take a bit of configuration but its been so long since i set up my server i have forgotten how to do it.

I'd recommend just extracting the php myadmin into a password protected directory in /var/www instead of installing it via the repos.

---

### Post by shoaibi on 2008-05-04
well thanks everyone, but i did the apt-get thing, i wanna know how to do a little conifguration that is left...

---

### Post by shoaibi on 2008-05-04
what abour the tasksel? is it in 8.04? does it require configuration if we install lamp-server via it?

---

### Post by scragar on 2008-05-04
[http://ayozone.org/2008/04/18/lamp-install-on-ubuntu-hardy/](http://ayozone.org/2008/04/18/lamp-install-on-ubuntu-hardy/)

```
sudo apt-get install apache2 php5-mysql libapache2-mod-php5 mysql-server php5-gd phpmyadmin
```

---

### Post by shoaibi on 2008-05-04
see, anime lover helps anime lover :P
Thanks scargar, thanks everyone..

---

