---
title: "mySQL installation..."
date: 2008-04-29
forum: Programming Talk
---

### Post by andyrue304 on 2008-04-29
Hi there.

I just installed LAMP on Hardy. Apache and PHP 5 are working, I've checked, but how do I verify that mySQL installed correctly?

During installation it asked me to set a password, which I did, but how do I find out the other information I need such as the database name?

Thanks
Andy

---

### Post by hyper_ch on 2008-04-29
you have to create one. Best is to install phpMyAdmin

---

### Post by andyrue304 on 2008-04-29
Thanks.

So what was the point of setting up a password in the installation process?

---

### Post by hyper_ch on 2008-04-29
> **andyrue304 said:**
> Thanks.

So what was the point of setting up a password in the installation process?

setting mysql root password... without it anybody could query it...

---

### Post by andyrue304 on 2008-04-29
Oh right!

Cheers m8!

EDIT: Acutually I think I have installed phpmyadmin already as I used this command to do the installation:

```
sudo apt-get install apache2 php5 mysql-server mysql-client phpmyadmin
```

So how do I use phpmyadmin?

Sorry I'm new to this, usually just stick to design :)

---

