---
title: "[SOLVED] Permission to write to /var/www/ ?"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Neureo on 2008-07-03
I got a lamp server up and running with Tasksel and found the right directory to save my files in (/var/www/), but when I try to save files in it, I get an error that says I don't have the permissions necessary to save the file. 

How to I grant these permissions? Thanks for your help!

---

### Post by Xerp on 2008-07-03
If the files are being written via the web application, then the user that Apache is running as needs to have permission to write to the directory.

e.g.

```
chown apache /var/www 
```

---

### Post by Bakerconspiracy on 2008-07-03
You need to move or copy the files as root (you have to be admin / know the root password in order to do this though). You can do this by adding sudo in front of the command you are using. EX. ```
sudo mv ./file /var/www/location/
```
 or alternatively, if you are trying to save text with gedit, open the text file with ```
sudo gedit filename&.
``` and you will have root power to save anywhere

---

### Post by Neureo on 2008-07-03
I tried doing **cd /var/www/** then **sudo gedit test.php**, and got the test file saved properly. Now when I try to open it, I get this: 

[IMG]http://i25.tinypic.com/351y611.png[/IMG]

What am I doing wrong?

---

### Post by Xerp on 2008-07-03
You need to PHP enable Apache

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Neureo on 2008-07-03
I used Tasksel to install a lamp server which is supposd to include apache, mysql, and php.

---

### Post by Xerp on 2008-07-03
> **Neureo said:**
> I used Tasksel to install a lamp server which is supposd to include apache, mysql, and php.

Then it didn't work as Apache doesn't know how to interpret PHP files :) Perhaps restart Apache? You could also post your Apache conf. You installed like this:

```
sudo tasksel install lamp-server
```

yes?

---

### Post by Neureo on 2008-07-03
Well...I did sudo tasksel, then selected LAMP server and hit enter, which I expect is the same thing. I did this only a few minutes ago and didn't change any settings.

---

### Post by PinkFloyd102489 on 2008-07-03
Chown it to the user and group www-data, which should be the user that Apache is running under.

---

### Post by Neureo on 2008-07-03
Ok, I did **chown www-data:www-data /var/www/**, then **cd /var/www/**, then **sudo gedit php_test.php** and wrote and saved my file, and now it appears to be working great! Thanks, guys.

---

