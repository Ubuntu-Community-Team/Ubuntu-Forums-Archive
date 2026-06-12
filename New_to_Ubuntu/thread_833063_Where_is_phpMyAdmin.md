---
title: "Where is phpMyAdmin"
date: 2008-06-18
forum: New to Ubuntu
---

### Post by arnold.pietersen on 2008-06-18
I have installed Joomla on my laptop, created a website and used gFTP to upload my file to my ISP. However, I need to transfer the database using phpMyAdmin.  Where do I find it on my laptop?

Thanks in advance

Arnold

---

### Post by milosz.galazka on 2008-06-18
You can install it using command
```
sudo apt-get install phpmyadmin
```
or just follow [http://wiki.cihar.com/pma/Quick_Install]("http://wiki.cihar.com/pma/Quick_Install")

---

### Post by ibutho on 2008-06-18
If you install phpmyadmin using apt-get, you can access it by going to 
```
http://localhost/phpmyadmin
```
If accessing it from a remote machine, just change localhost to the hostname of the machine where phpmyadmin is installed.

---

### Post by arnold.pietersen on 2008-06-18
Hi ibutho & milosz.galazka

It worked.  Thanks a lot.

Where do I get the username and password?

Regards

Arnold

---

### Post by fatality_uk on 2008-06-18
The username and password for your MySQL database!

---

### Post by milosz.galazka on 2008-06-18
As I remember you can use username/password that you use to connect mysql database

---

### Post by arnold.pietersen on 2008-06-18
Guys

Thanks a lot again

The username was root and there was the password was blank.

Thanks you

---

### Post by fatality_uk on 2008-06-18
Change that ASAP!!! A default DB install is not secure until

---

