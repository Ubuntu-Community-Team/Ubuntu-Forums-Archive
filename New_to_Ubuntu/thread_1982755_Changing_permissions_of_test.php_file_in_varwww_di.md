---
title: "Changing permissions of test.php file in /var/www directory"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-05-19
I am installing php on my machine from:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)
and I need some help with an instruction:
> Checking PHP 5 installation 
In  /var/www , create a text file called "test.php", grant the world (or,  at least, Ubuntu user "apache") permission to read it, write in it the  only line: "<?php phpinfo(); ?>" (without the quotation marks)  then, with your web browser, go to the URI "[http://localhost/test.php](http://localhost/test.php)": if you can see a description of PHP5 configuration, it proves PHP 5 works with Apache. 
The directory listing of the /var/www directory is:
```

glenn@acer:/var/www$ ls -al
total 16
drwxr-xr-x  2 root root 4096 May 19 21:14 .
drwxr-xr-x 14 root root 4096 May 19 20:52 ..
-rw-r--r--  1 root root  177 May 19 20:52 index.html
-rw-r--r--  1 root root   20 May 19 21:14 test.php
-rw-r--r--  1 root root    0 May 19 21:14 test.php~
glenn@acer:/var/www$

```Help! How do I change permission on the file, and what do I change it to? And what does the tilde mean after the file name?

---

### Post by Cheesemill on 2012-05-19
To change permission:
```
sudo chown www-data.www-data test.php
```

The file test.php~ is a previous version of test.php
When you edit a file using nano or vim it creates a backup of the previous version and saves it as the same name but with a tilde at the end.

---

### Post by Senior_Buckethead on 2012-05-19
Cheers Cheesemill.

---

