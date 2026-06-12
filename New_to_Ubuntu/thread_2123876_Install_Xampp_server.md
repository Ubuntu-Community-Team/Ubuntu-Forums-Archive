---
title: "Install Xampp server"
date: 2013-03-09
forum: New to Ubuntu
---

### Post by Susss on 2013-03-09
I have extracted files to my /opt directory with root privilages but wen i try to install it using( [FONT=Courier]/opt/lampp/lamppstart) this code it replies ([/FONT]You need to start XAMPP as root!) M i doing something rong??

---

### Post by Cheesemill on 2013-03-09
As it says you need to run the command as root...
```
sudo /opt/lampp/lamppstart
```

Is there any reason you are using Xampp instead of the standard LAMP stack in the Ubuntu repositories?

---

### Post by Susss on 2013-03-09
oo yes......i am currently learnin php and mysql so i needed a server....so m using lampp....Isnt that ok??

---

### Post by mastablasta on 2013-03-09
LAMP is easy to install and use.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

it's easir to do it liek this than messa round with XAMMP

---

### Post by bro on 2013-03-09
I use xampp too. It's easy to backup and migrate through systems and installs and easy to configure with all stuff in one place. 

Just: sudo /opt/lampp/lamp start and it will work.

---

### Post by bro on 2013-03-09
In addition you might want to make a symbolic link from your htdocs to a folder in your /home that you can easily edit. Search this forum there is a clear explanation somewhere on xampp

---

### Post by fiodev on 2013-03-09
apt-get install tasksel
tasksel
install lamp server
apt-get install phpmyadmin after
this is what I use for php and mysql works great

---

### Post by itrogers on 2013-03-09
> **fiodev said:**
> apt-get install tasksel
tasksel
install lamp server
apt-get install phpmyadmin after
this is what I use for php and mysql works great

From personal experience I can confirm that this is the most simple way to set up a local web hosting environment.

---

### Post by Cheesemill on 2013-03-09
> **fiodev said:**
> apt-get install tasksel
tasksel
install lamp server
apt-get install phpmyadmin after
this is what I use for php and mysql works great

You don't even need to install tasksel, you can get the same result with...
```
sudo apt-get install lamp-server^ phpmyadmin
```

---

### Post by Susss on 2013-03-10
Now i have instaled xamp but i cant get aces to htdocs..what to do?

---

### Post by bro on 2013-03-10
You can read the first post from link below. It explains how to install and then create a symbolic link to a place you do have access. /opt is only accessible with superuser permissions. [http://ubuntuforums.org/showthread.php?t=223410&highlight=Xampp](http://ubuntuforums.org/showthread.php?t=223410&highlight=Xampp)

---

### Post by paprin on 2013-03-20
Do you install WordPress in your Xampp server?

---

### Post by paprin on 2013-03-20
You can try this path in your address bar: [COLOR=#008000]C:\xampp\htdocs[/COLOR]. It will be redirected you to htdocs. file.

---

### Post by paprin on 2013-03-20
Or, Just select [COLOR=#008000]start[/COLOR] button and select [COLOR=#00ff00]search[/COLOR] from start menu. From the left side of the window make sure to look in [COLOR=#006400]Local drive C:\ or the drive name[/COLOR] where you install xampp. Then in the blank field of "All or part of the file name" put: [COLOR=#008000]htdocs[/COLOR] , click on the search button. You will probably find two result. Choose the result of [COLOR=#008000]C:\xampp[/COLOR]. Now open it and access your necessary files.

---

