---
title: "Help! Messed up installing LAMP"
date: 2013-05-13
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2013-05-13
So,
I tried installing LAMP but messed up on the MySQL bit. 

Here is the tutorial I used:

[http://www.howtoforge.com/ubuntu_lamp_for_newbies](http://www.howtoforge.com/ubuntu_lamp_for_newbies) 

Here is what Step 3 says:

Step 3. This is where things may start to get tricky. Begin by typing the following into Terminal:
 mysql -u root

That's exactly where it gets tricky. Here's what I get when I type that command:

ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

Sooo... I have Apache installed and PHP installed. Now I just need MySQL. Any help would be GREATLY appreciated.

---

### Post by Ranger_Joe on 2013-05-13
I seemed to have fixed it by reconfiguring (resetting root password for MySQL). I did so by entering this in the terminal:


$ sudo dpkg-reconfigure mysql-server-5.5

---

### Post by mastablasta on 2013-05-14
i think procedures have changed since 2007 (date of that tutorial you posted) and are now much easier.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
[http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/](http://www.unixmen.com/install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat/)

there is even one line command that does it all that bypassing tasksel instalation.
sudo apt-get install lamp-server^

i suggets you install a few web gui applicaitons. they are much easier to udnerstand for us newbiew in my opinion.

---

