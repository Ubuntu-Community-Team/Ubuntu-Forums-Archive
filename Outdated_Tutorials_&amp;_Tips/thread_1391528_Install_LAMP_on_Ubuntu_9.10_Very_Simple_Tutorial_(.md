---
title: "Install LAMP on Ubuntu 9.10 Very Simple Tutorial (10 Steps)"
date: 2010-01-26
forum: Outdated Tutorials &amp; Tips
---

### Post by jamestrowbridge on 2010-01-26
[LIST=1]
[*]Go to Applications --> Accessories --> Terminal

[*]Copy and Paste the Following into the Terminal and Press Enter to Execute:
```
sudo apt-get install libapache2-mod-auth-mysql php5-mysql apache2 php5 libapache2-mod-php5 mysql-server
```

[*]apt-get may ask you:
> Do you want to continue [Y/n]?
Press Y and then enter to continue

[*]It should automatically prompt you to enter the MySQL root password, please do so (then confirm it as it asks)

[*]If you will only be accessing MySQL via PHP or Terminal on this server, go to the next step, otherwise:
Copy and Paste the Following into the Terminal and Press Enter to Execute:
```
sudo gedit /etc/mysql/my.cnf
```
Go to the line containing: bind-address = 127.0.0.1
(Use Ctrl+F to Search for it)
Replace 127.0.0.1 with the IP Address of the server's interface that you will connect through to access MySQL from another computer, Save and Exit gedit

[*]Copy and Paste the Following into the Terminal and Press Enter to Execute:
```
sudo gedit /etc/php5/apache2/php.ini
```
Either find the line: ```
;extension=mysql.so
```
And uncomment it by removing the: ```
;
```
or if that line doesn't exist, insert on a new line in the 'Dynamic Extensions' area:
```
extension=mysql.so
```
Save and Exit gedit

[*]Copy and Paste the Following into the Terminal and Press Enter to Execute:
```
sudo /etc/init.d/apache2 restart
```

[*]Copy and Paste the Following into the Terminal and Press Enter to Execute:
```
sudo nautilus /var/www
```
Create a new file in there called: ```
test.php
```
Open it with gedit and fill it with:
```
<?php
phpinfo();
?>
```
Save and Exit gedit

[*]Open a browser and browse to: ```
http://localhost/test.php
```

[*]If it opens up some purple boxes filled with a bunch of information, you can give yourself a real big pat on the back -- maybe even kiss your own cheek ...[Tadow]("http://www.urbandictionary.com/define.php?term=Tadow") you have installed LAMP on Ubuntu 9.10
[/LIST]

---

### Post by alfplayer on 2010-01-27
Isn't it easier using tasksel ?

---

### Post by od3n on 2010-01-28
wow simple and quick one.

---

### Post by adeypoop on 2010-02-05
nice one, thanks for sharing

---

### Post by mujismile on 2010-06-21
Many thanks..
It works for UBUNTU 10.04 as well..
;)

---

### Post by Forming on 2010-06-25
Nice one.

---

### Post by webvet on 2010-07-13
Thanks - worked perfectly even for a newbie like me!  :D

---

### Post by thahir1986 on 2010-07-14
thanks to shared with us

---

### Post by Ghost_Mazal on 2010-12-23
Lo guys. I don't know what LAMP stands for.

What I need is a running Apache with php and mysql server.
Will this work for me on 10.04 64bit Desktop version ?

---

### Post by tornadof3 on 2010-12-23
LAMP: Linux, Apache, MySQL, PHP

Should work fine for you.

---

