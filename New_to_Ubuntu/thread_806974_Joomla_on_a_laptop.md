---
title: "Joomla on a laptop"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Humanum on 2008-05-25
Hi,


I'm trying to install Joomla on my laptop... I don't have a website, I just want to use it on local...

Any help will be appreciated...

I would like to know how to do it and how to configure it using lighttp or apache...

Cheers...

---

### Post by quelx on 2008-05-25
This will probably help: [https://help.ubuntu.com/community/Joomla](https://help.ubuntu.com/community/Joomla)

---

### Post by Humanum on 2008-05-26
Thank you...

Unfortunately I'm still having problems due to the fact that the I'm using Hardy Heron while the documentation is for older Ubuntu versions...

I'll try to read more about the process and see how to carry on as I'm a newcomer in Linux world...

Cheers

---

### Post by twright on 2008-05-26
the tutorial should work for hardy

---

### Post by indytim on 2008-05-26
Can you be a bit more specific on what kind of problems you are having (mysql, apache, php, joomla) ?

IndyTim

---

### Post by Humanum on 2008-05-26
For the time being my problems are mainly related to mysql and phpmyadmin...

Configuring apache2, I've already created my database... But I don't know how to access phpmyadmin... Whenever I try : [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) the display is : Forbidden...

Thanks for helping...

---

### Post by indytim on 2008-05-26
Sounds like you've got a permission problem.  Suggest you change the group and owner of the directory that you have phpmyadmin is to your user id
```


$sudo chgrp /var/www/phpmyadmin <your user id>
$sudo chown /var/www/phpmyadmin <your user id>


```

I'm using the directory path as an illustration.  You will need to insert the correct path.

While you're at it, you might want to do the same for /var/www . This will set you as the owner of the website with full access.

Hope this helps,

IndyTim

---

### Post by Humanum on 2008-05-26
> **indytim said:**
> Sounds like you've got a permission problem.  Suggest you change the group and owner of the directory that you have phpmyadmin is to your user id
```


$sudo chgrp /var/www/phpmyadmin <your user id>
$sudo chown /var/www/phpmyadmin <your user id>


```

I'm using the directory path as an illustration.  You will need to insert the correct path.

While you're at it, you might want to do the same for /var/www . This will set you as the owner of the website with full access.

Hope this helps,

IndyTim


this is what I'm getting :

1) Since the phpmyadmin directory is in /etc/phpmyadmin/, I've tried to type :

sudo chown /etc/phpmyadmin/ dany (which is my user name) and i'm receiving the following message : Invalid group /etc/phpmyadmin

and when i typed chown /var/www/ dany, the message is missing operand after  /var/www/

---

