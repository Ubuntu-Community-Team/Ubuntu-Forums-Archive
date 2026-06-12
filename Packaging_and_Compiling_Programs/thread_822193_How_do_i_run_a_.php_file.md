---
title: "How do i run a .php file"
date: 2008-06-08
forum: Packaging and Compiling Programs
---

### Post by nebu on 2008-06-08
I got a script.php file.... how do i compile and run this script....

---

### Post by forger on 2008-06-08
**only do this if it's your own script** - if it's not, please consult someone to check it out before trying it!

open up gnome terminal and execute:
```
sudo apt-get install php5-cli
```

then use the "cd" command to head to your php5 script directory, and do:
```
php your-file.php
```

---

### Post by ad_267 on 2008-06-08
A php script is usually used to build websites and is interpreted by a web server. If you want to run a php script yourself you can install the php5-cli package. If you want to use this php script to test and build a website then you will want to install the apache2 web server and php.

---

### Post by comandrei on 2008-06-08
> **nebu said:**
> I got a script.php file.... how do i compile and run this script....
You can't compile a PHP script. You can use a byte-code cacher, but you can't compile it

---

### Post by id1337x on 2008-06-10
Open a gnome-terminal and do something like this:

```
sudo apt-get install php5
cd mylocation
php myfile.php
```

Also you should probably do a web server if you want to use PHP for the conventional use (designing websites and databases).

```
sudo apt-get install apache2
sudo apt-get install mysql-client mysql-server php5-mysql
```

PHP's best used with Apache.
[http://www.apache.org/](http://www.apache.org/)

---

### Post by khurtsiya on 2009-06-11
I have installed both - PHP and Apache.

Now I need to run file index.php so it looks like in my browser like I visit the site.

How should I do this?

TIA

Michael

---

### Post by khurtsiya on 2009-06-11
Found how to do this here [http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/installing-php5-and-apache-on-ubuntu/)

But /var/www is located in root folder, how can I obtain same at my home directory?

---

### Post by ravikanth.vva on 2011-05-07
i got nothing from the link you gave....can any one help me how to run my php file in firefox....i have php and apache installed...this is my first php script

---

### Post by Agentkiller4 on 2011-05-16
```
php myfile.php > myfile.html && firefox myfile.html
```

This code in terminal will take the php file and process it into a proper file, then opens it in firefox.

This simulates what a web server would do with said php script.

Dependencies: php5-cli, php5

---

### Post by Petrolea on 2011-05-19
Since you're a beginner, I recommend that you install a simple server to run php files called XAMPP (actually it's much more than just that, but lets leave that behind). Tutorials can be found all over the internet :)

---

### Post by ApOgEEs on 2011-05-27
> **nebu said:**
> I got a script.php file.... how do i compile and run this script....

You don't have to compile a php script. However, if you still have to compile it for some reason, you may look for phc: [http://www.phpcompiler.org/](http://www.phpcompiler.org/)

To run a php script, install php5
```
$ sudo apt-get install php5
```

then you can run it using this command on your terminal:
```
$ php script.php
```

---

