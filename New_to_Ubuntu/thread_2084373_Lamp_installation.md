---
title: "Lamp installation"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by horgag on 2012-11-15
Hi,
IM installing LAMP server on a Ubuntu server. Im following the instrutions from [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp). The apache2 install seems ok. I get the IT WORKS webpage in the localhost. I then installed php5 using the command and then created the info,php file in /var/www directory. But when i go to localhost/info.php i get a message saying what should FF do with this file (gedit default). Absolute beginner!!!! Dont know what to do.

---

### Post by pkadeel on 2012-11-15
> **horgag said:**
> Hi,
IM installing LAMP server on a Ubuntu server. Im following the instrutions from [http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp](http://www.howtoforge.com/installing-apache2-with-php5-and-mysql-support-on-ubuntu-12.04-lts-lamp). The apache2 install seems ok. I get the IT WORKS webpage in the localhost. I then installed php5 using the command and then created the info,php file in /var/www directory. But when i go to localhost/info.php i get a message saying what should FF do with this file (gedit default). Absolute beginner!!!! Dont know what to do.
If you were following that guide then most probably you skipped the apache2 restart.
Do it
```
sudo service apache2 restart
```

---

### Post by Lars Noodén on 2012-11-15
Also, is mod_php active?

```

sudo a2enmod php5

```

---

### Post by pkadeel on 2012-11-15
> **Lars Noodén said:**
> Also, is mod_php active?

```

sudo a2enmod php5

```
I have noticed that when libapache2-mod-php5 is installed via apt-get, it gets enabled by default.

---

### Post by mörgæs on 2012-11-15
In case someone else reads this thread, I would recommend installing with the commands

```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

rather than the link in first post.

---

### Post by monkeybrain2012 on 2012-11-15
> **mörgæs said:**
> In case someone else reads this thread, I would recommend installing with the commands

```
sudo apt-get install tasksel
sudo tasksel install lamp-server
```

rather than the link in first post.

I would not recommend tasksel, it killed my system last time. I install via apt-get and all is fine. The link is ok but I am not sure why he su to root instead just using sudo.

---

### Post by horgag on 2012-11-15
> **monkeybrain2012 said:**
> I would not recommend tasksel, it killed my system last time. I install via apt-get and all is fine. The link is ok but I am not sure why he su to root instead just using sudo.

Thanks for the response, that problem has been solved. The only thing left is  icant log into phpmyadmin. I can log into mysql through the terminal. Any ideas!!!?

---

### Post by CharlesA on 2012-11-15
> **monkeybrain2012 said:**
> I would not recommend tasksel, it killed my system last time. I install via apt-get and all is fine. The link is ok but I am not sure why he su to root instead just using sudo.

Old guide is old. My bet is they didn't want to keep using sudo.

In any case, tasksel is fine as long as you don't uncheck anything. I've used it to install many boxes and haven't run into any problems with it.

> **horgag said:**
> Thanks for the response, that problem has been solved. The only thing left is  icant log into phpmyadmin. I can log into mysql through the terminal. Any ideas!!!?

It should use the same password that you use for mysql.

---

### Post by horgag on 2012-11-15
> **CharlesA said:**
> Old guide is old. My bet is they didn't want to keep using sudo.

In any case, tasksel is fine as long as you don't uncheck anything. I've used it to install many boxes and haven't run into any problems with it.



It should use the same password that you use for mysql.

i am using the same password as mysql but nothing seems to happen on the phpmyadmin loginpage....it just continually trying to connect..no error.
cheers

---

### Post by pkadeel on 2012-11-16
> **horgag said:**
> i am using the same password as mysql but nothing seems to happen on the phpmyadmin loginpage....it just continually trying to connect..no error.
cheers
My guess is that you didn't select MySQL as the database to be used with phpmyadmin during the installation of phpmyadmin. During its installation it appears that it is selected by default however it is not and you have to press spacebar to actually select it. Did you do that? If not then that is the problem.

---

### Post by horgag on 2012-11-16
> **horgag said:**
> i am using the same password as mysql but nothing seems to happen on the phpmyadmin loginpage....it just continually trying to connect..no error.
cheers


I selected the apache2 server by pressing the space bar. just wondering when i ran the command sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf

i got the following message

failed to create a symbolic link /etc/apache2/conf.d/phpmyadmin.conf : File already exitts

Is this wrong??

---

### Post by pkadeel on 2012-11-17
> **horgag said:**
> I selected the apache2 server by pressing the space bar. just wondering when i ran the command sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf

i got the following message

failed to create a symbolic link /etc/apache2/conf.d/phpmyadmin.conf : File already exitts

Is this wrong??
That link is already present otherwise you couldn't have browsed to the login page.
Are you sure you have also installed the php5-mysql extenssion. if not then
```

sudo apt-get install php5-mysql
sudo service apache2 restart

```

---

