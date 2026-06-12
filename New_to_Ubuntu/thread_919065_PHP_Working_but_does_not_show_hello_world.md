---
title: "PHP Working but does not show hello world"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by disappearedng on 2008-09-13
Hi everyone
I am trying to learn php right now: I have installed everything that the documentation told me to but I have encountered the following problem:

Please look at this:
```
<html> 
<head> 
  <title>Hello, world</title> 
</head> 
<body>
  <h1> 
    <?php
    print "Hello, World!";
    ?> 
  </h1> 
</body> 
</html>

```
On my browser when I access 127.0.0.1 (localhost), I see the title Hello, world.

However, I do not see HELLO WORLD printed on the actual body, which means that <?php?> did not work. I have installed php5, the latest version TODAY before I restarted my computer.

How might I go about finding the errors here?

Please help
\

---

### Post by howlingmadhowie on 2008-09-13
it sounds like libapache2-mod-php5 isn't installed.
try:

```
sudo apt-get install libapache2-mod-php5
```

and then restart apache:

```
sudo /etc/init.d/apache2 restart
```

---

### Post by disappearedng on 2008-09-13
```

disappearedng@disappearedng-ubuntu-client:~$ sudo apt-get install libapache2-mod-php5
[sudo] password for disappearedng: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libapache2-mod-php5 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by hyper_ch on 2008-09-13
and if it still does not work then run
```

sudo a2enmod php5
sudo /etc/init.d/apache2 restart

```

---

### Post by howlingmadhowie on 2008-09-13
curious. can you try installing php5-cli and then running your program from the command line?

---

### Post by disappearedng on 2008-09-13
```

disappearedng@disappearedng-ubuntu-client:~$ sudo a2enmod php5
This module is already enabled!
disappearedng@disappearedng-ubuntu-client:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                         [ OK ] 

```

Still doesn't work. I have done that already.

I have installed php5-cli. How do I run it?

---

### Post by hyper_ch on 2008-09-13
did you save the file as .php ?

simplest way to test is this:

phpinfo.php
[php]
<?php phpinfo(); ?>
[/php]

---

### Post by howlingmadhowie on 2008-09-13
i know what's wrong. does the filename you've chosen end with .php ?

----edit----

i see hyper_ch got there first

---

### Post by disappearedng on 2008-09-13
OMG I M SUCH AN IDIOT.

I REALLY FORGOT TO SAVE IT AS .php. 

thanks so much for the help. I really appreciate it. 

(I am learning from scratch and my book hasn't taught me to save it yet.).

---

### Post by howlingmadhowie on 2008-09-13
don't mention it. you can run php from the command line (after installing php5-cli) by entering:

```
php name_of_program.php
```

---

