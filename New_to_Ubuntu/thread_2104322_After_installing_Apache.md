---
title: "After installing Apache"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by Lagbehind on 2013-01-12
I have installed Apache2 and I have checked that it is running:: 	   # ps -u 



It seems to be running and when I put [http://127.0.0.1/](http://127.0.0.1/) I get the "It works" message.  But I haven't managed to understand yet where I put the files or file structure of files that I wish to run locally.  Such as, in Windows placing putting php files and running apache is quite straight forward.


Where for example would I put a simple file containing stuff like....



<html> 
<head> 
<title>A PHP script including HTML</title> 
</head> 
<body> 
<b> 
<?php 
echo "Hello World"; 
?> 
</b> 
</body> 
</html>


:confused:

---

### Post by Cheesemill on 2013-01-12
Content for the default site lives in the /var/www directory.

[https://help.ubuntu.com/community/ApacheMySQLPHP#Using_Apache](https://help.ubuntu.com/community/ApacheMySQLPHP#Using_Apache)

---

### Post by stmiller on 2013-01-12
Default is:

/var/www/


```
$ cat /var/www/index.html 
<html><body><h1>It works!</h1>
<p>This is the default web page for this server.</p>
<p>The web server software is running but no content has been added, yet.</p>
</body></html>

```

---

### Post by Lagbehind on 2013-01-13
Ok so I am getting somewhere but still don't want to make changes because I don't understand what the significance is of what I'm seeing and also what I might change. Too much is new at once so please bear with me.

As I have said before typing the following:-

[http://127.0.0.1/](http://127.0.0.1/) or [http://localhost/](http://localhost/)

...... gives the following message: 

It works!

This is the default web page for this server.

The web server software is running but no content has been added, yet.

However, I went to the link that you listed below:

[https://help.ubuntu.com/community/Ap...P#Using_Apache](https://help.ubuntu.com/community/Ap...P#Using_Apache)

and tried the restart - haveing been keen to know how to restart Apache (if you know what I mean).  So I typed:


sudo /etc/init.d/apache2 restart

and got the following:
=======================================================================================================================
 * Restarting web server apache2                                                apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 ... waiting apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
                                                                         [ OK ]
=======================================================================================================================

Why is it using 127.0.1.1 and not 127.0.0.1?  I need to understand before I attempt to make futher changes if I need to, because reading further on the page it goes on to talk about running:


sudo nano /etc/apache2/conf.d/fqdn


"If you get this error:

apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName

then use a text editor such as "sudo nano" at the command line or "gksudo gedit" on the desktop to create a new file, etc"

Please help and explain?

---

### Post by Cheesemill on 2013-01-13
That error is nothing to worry about, it's just a warning.

Doing a quick search for the warning message gives loads of results with a method to fix this, for example...
[http://stackoverflow.com/questions/9541460/httpd-could-not-reliably-determine-the-servers-fully-qualified-domain-name-us](http://stackoverflow.com/questions/9541460/httpd-could-not-reliably-determine-the-servers-fully-qualified-domain-name-us)

Your web server will work fine whether you do this or not, it's just a warning not an error.

---

### Post by Lagbehind on 2013-01-13
Ok  thanks. But how would I:

1. check that PHP5 is working?
2. do I put the pages - do they go under var/www or etc/apache2/config.d?
3. need to update a configuration file (if so which) to tel Apache where my files are and I am using php5?

Sorry these may be very simple questions, I just very disorientated, it is so different from 30 yrs of MS Windows.

---

### Post by Cheesemill on 2013-01-13
The page I linked to earlier tells you all of this and more, I suggest reading through all of it.

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

