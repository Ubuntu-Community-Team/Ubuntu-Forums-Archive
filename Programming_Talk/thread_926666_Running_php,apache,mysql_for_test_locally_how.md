---
title: "Running php,apache,mysql for test locally how?"
date: 2008-09-22
forum: Programming Talk
---

### Post by extruct on 2008-09-22
Hello all. I'm a web developer. In WinXP I used WAMP as a test server, it didn't harm my security since it run locally and was accessible only from localhost + it was easy to install no configuration of apache, php, mysql just click`n`go.
Is there a Linux package like WAMP? I just need to test my scripts, I don't want to run server and make it accessible for all, just my pc.
Thanks.

---

### Post by leg on 2008-09-22
Install mysql php etc through synaptic. You may need to do some config depending on your needs. I think there is also a meta-package (lamp-server or something). Don't forget to install other things you need like mod-rewrite etc.

---

### Post by ianhaycox on 2008-09-22
It's called LAMP.

Looking at [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP") you should just need

```
sudo tasksel install lamp-server

```

Then just hit [http://localhost/](http://localhost/) with all your files stored in /var/www

---

### Post by cb951303 on 2008-09-22
also you may enable userdir which lets you place your docs to /home/userName/public_html by default which is accessed from [http://localhost/~userName](http://localhost/~userName). This way you don't have to use sudo every time you want to move something to /var/www

```

sudo a2enmod userdir

```

---

### Post by extruct on 2008-09-22
Well I found xampp to be very close to WAMP.
Thanks anyway, Ill try it now.

---

