---
title: "phpMyAdmin"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by carrickdrive on 2008-05-21
Ubuntu 8.04LST
I have been following tutorials re installing php and apache.  I have apache working as it says in the browser "It Works".  However I cannot get phpMyAdmin to come up as it does in Windows or on the 7.10 install.  I notice that it is now in share folder and not in the www folder under var.

Can any one help

---

### Post by quelx on 2008-05-21
You need to create a symlink from /etc/phpmyadmin/apache.conf to /etc/apache2/conf.d/

```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
```

restart apache

```
sudo /etc/init.d/apache2 reload
```

then browse to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

---

### Post by carrickdrive on 2008-05-21
> **quelx said:**
> You need to create a symlink from /etc/phpmyadmin/apache.conf to /etc/apache2/conf.d/

```
sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf.d/phpmyadmin.conf
```

restart apache

```
sudo /etc/init.d/apache2 reload
```

then browse to [http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Many thanks that worked.  
How do I set the apache2.conf file to give the correct servername.  I have tried a couple of ways.

apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName

---

### Post by quelx on 2008-05-21
add a to the line 127.0.0.1 in your /etc/hosts. for example 
```
127.0.0.1 localhost myfulldomain.name
```

or add a line to the /etc/apache2/apache2.conf

```
ServerName myfulldomain.name
```

the host file is probably the way to go

---

### Post by carrickdrive on 2008-05-21
> **quelx said:**
> add a to the line 127.0.0.1 in your /etc/hosts. for example 
```
127.0.0.1 localhost myfulldomain.name
```

or add a line to the /etc/apache2/apache2.conf

```
ServerName myfulldomain.name
```

the host file is probably the way to go

Super thanks I clocked it and did it with gedit and it came up without an error.

Many thanks for your help.

---

