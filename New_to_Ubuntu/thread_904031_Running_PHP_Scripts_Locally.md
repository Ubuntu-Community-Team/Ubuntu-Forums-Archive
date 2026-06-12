---
title: "Running PHP Scripts Locally"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by abeisgreat on 2008-08-28
I'm a web developer and I do most of my work in php, and I always find it annoying to have to upload my files to the server each time I need to test.

Is there some application, preferably lightweight, which would allow me to test my php scripts locally?

I imagine it is doable by running a server of sorts on my computer, so any tutorials or how-tos would be great :D

---

### Post by erichmj on 2008-08-28
You could either do the server install through apt-get or you could download xampp [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html) just follow the instructions on the site to set it up and everything is taken care of for you.

---

### Post by abeisgreat on 2008-08-28
And downloading xampp and installing php5 will allow me to run my scripts locally?

---

### Post by erichmj on 2008-08-28
xampp comes with php5 already. but yes to answer your question it will.

---

### Post by abeisgreat on 2008-08-28
Alright I'll try xampp

---

### Post by Vadi on 2008-08-28
Just install [php-cli]("apt:php5-cli")? Then you can do "php myscript.php".

---

### Post by abeisgreat on 2008-08-28
now thats more like it, I'll try php-cli, and if it works good i wont get xampp

EDIT: Is there anyway I can see the outcome of php-cli in a web browser?

---

### Post by hyper_ch on 2008-08-29
> **abeisgreat said:**
> EDIT: Is there anyway I can see the outcome of php-cli in a web browser?

Installa apaches and php5 module

```

sudo apt-get install apache2 libapache2-mod-php5

```

and then

```

sudo a2enmod php5

```

---

### Post by abeisgreat on 2008-08-30
> **hyper_ch said:**
> Installa apaches and php5 module

```

sudo apt-get install apache2 libapache2-mod-php5

```

and then

```

sudo a2enmod php5

```


So I installed that and when I try to load it I get an error

so i uninstalled it Im gonna try xampp

EDIT: so I got xampp up and running but now none of my scripts execute, I get
"Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0"
I assume this is because of permissions in the htdocs folder, is there a way I can load files NOT from the dir?

---

