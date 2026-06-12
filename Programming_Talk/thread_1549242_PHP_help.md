---
title: "PHP help"
date: 2010-08-09
forum: Programming Talk
---

### Post by yeohchan on 2010-08-09
I am recently learning php, however when I was trying out forms with php it won't work. 

I made a html file and a php file, which the html file would have a submit button and would transfer data to the php file. Whenever I try it it will tell me to download the php file.

Here is what I mean:
[http://i942.photobucket.com/albums/ad269/yeohchan/Screenshot.png](http://i942.photobucket.com/albums/ad269/yeohchan/Screenshot.png)

Can anyone resolve the problem. Thanks

---

### Post by Bachstelze on 2010-08-09
You can't run PHP files like that. You need to install a web server on your machine.

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)
[https://help.ubuntu.com/10.04/serverguide/C/php5.html](https://help.ubuntu.com/10.04/serverguide/C/php5.html)

---

### Post by Truemedia on 2010-08-09
XAMPP is a web server that will work on ubuntu

[http://www.apachefriends.org/en/xampp-linux.html]("http://http://www.apachefriends.org/en/xampp-linux.html")

---

### Post by Hellkeepa on 2010-08-12
HELLo!

Use the web server provided by your repository instead, will give you a LOT less headaches.
```
sudo apt-get install libapache2-mod-php5
```
That should install all of the necessary packages.

Happy codin'!

---

