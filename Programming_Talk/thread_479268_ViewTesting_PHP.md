---
title: "View/Testing PHP"
date: 2007-06-20
forum: Programming Talk
---

### Post by phizikal on 2007-06-20
Ok, I am currently working on a website. I wrote a emailer script and a MD5 hasher, but I am new to ubuntu. I would test these on a web host, but I currently don't have money, and I also have some scripts that violates the terms of free host companys.

Is there anyway I can test these files on my own computer without a host.

Please and thank you's!

---

### Post by scribles on 2007-06-20
Yes you can.

[LIST=1]
[*]Install Apache, PHP and any other modules you need.```
sudo apt-get install apache php5
```
[*]Put your files in /var/www
[*]Point your browser to [http://localhost/](http://localhost/)
[/LIST]

---

### Post by phizikal on 2007-06-20
Okay, I tried using that command to install it. And I got an error. 

Reading package lists... Done
Building dependency tree... Done
Package apache is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package apache has no installation candidate

---

### Post by scribles on 2007-06-20
opps... try
```
sudo apt-get install apache2 php5
```

---

### Post by phizikal on 2007-06-20
Yummy! Thanks my friend.
Much appreciated,

---

### Post by phizikal on 2007-06-20
BTW, it is saying I do not have permissions to copy to the WWW folder.

Sorry about that... =/

---

### Post by scribles on 2007-06-20
you have 3 options
[LIST=1]
[*]use sudo to copy files into the folder as root (yuk) ```
sudo cp filename /var/www/ 
```
[*]make yourself the owner of /var/www (only a good idea on a testing only server) ```
sudo chown username /var/www
```
[*]or configure apache so that is serves files from a different folder. this is the best option but more time consuming.
[/LIST]

---

### Post by phizikal on 2007-06-20
Thank you.

Is there a way I can have permissions on everything? I dont wanna have to manualy make myself the owner on every file.

---

### Post by phizikal on 2007-06-20
Also, you know how I can set up a mySQL database?

---

### Post by scribles on 2007-06-20
The file system permissions are one of the things that make Linux very secure. One of the reasons viruses / spyware do so much damage to Windows is because most people do everything as Administrator which is very unsafe. I recomend that you give using sudo to elivate your privleges and chmod / chown to change permission only when you have to a chance. It won't take long before it seems second nature and you will be much better off for it.

---

### Post by phizikal on 2007-06-20
Mmmk, I understand that now.

And about setting up a MySQL database?

---

### Post by Occasionally Correct on 2007-06-20
> **phizikal said:**
> Also, you know how I can set up a mySQL database?

[I used this article](https://help.ubuntu.com/community/ApacheMySQLPHP) when I was setting up a small testing server on my computer. It's a bit of a read, but it went by pretty quickly and it worked very well. :)

---

### Post by scribles on 2007-06-20
```
sudo apt-get install mysql-server php5-mysql
``` will install the server and the mysql plugin for php. also phpmyadmin is handy for managing databases
```
sudo apt-get install phpmyadmin
```

---

### Post by phizikal on 2007-06-20
um the second command didn't install correctly.

=/

---

### Post by scribles on 2007-06-20
Do you have the Universe repository enabled? If not take a look at [https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

