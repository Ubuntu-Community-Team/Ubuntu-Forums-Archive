---
title: "I need help to set up php"
date: 2008-12-05
forum: Programming Talk
---

### Post by hoboy on 2008-12-05
I have used lots of time to make php work on ubuntu without a success.
 I used NetBeans
I have follow this link
[http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html](http://www.netbeans.org/kb/docs/php/configure-php-environment-ubuntu.html)
then create a little project when I run my browser point to

[http://localhost/PhpProject1/index.php](http://localhost/PhpProject1/index.php)
I always get  the  error 
404 Not Found

thanks

---

### Post by dwhitney67 on 2008-12-05
I had a similar problem once before.  I do not know if what I did to resolve the issue was correct or not, but this is what I did:

1.  sudo vi /etc/apache2/sites-available/default

2.  Change the following:
```

     #DocumentRoot /var/www
     DocumentRoot /home/user

```
3.  Change the following:
```

     #<Directory /var/www>
     <Directory /home/user>

```
4.  Save the file.

Replace the "user" above with your userid.

That should do it.  Try running your script again via the browser.

---

### Post by hoboy on 2008-12-05
when I run sudo /etc/init.d/apache2 restart

I get the following error

test@ubuntu:~$ gksudo gedit /etc/apache2/sites-available/mysite 
test@ubuntu:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

---

### Post by snova on 2008-12-05
> **hoboy said:**
> test@ubuntu:~$ sudo /etc/init.d/apache2 restart
 * Restarting web server apache2                                                (98)Address already in use: make_sock: could not bind to address 0.0.0.0:80
no listening sockets available, shutting down
Unable to open logs

It looks like another server is already trying to bind to port 80, so Apache can't. Try the 'netstat -l' command to find out what.

I don't know what the last line ("Unable to open logs") means.

---

### Post by hoboy on 2008-12-05
I have installed xampp now the problem is how to set ubuntu to deploy php projects under it.now when I create php project in netbeans then run it inside the ide I get the following error
The requested URL /NetBeansProjects/index.php was not found on this server.

---

### Post by hoboy on 2008-12-05
problem is solved

---

### Post by dwhitney67 on 2008-12-05
> **hoboy said:**
> problem is solved
Thanks for sharing your solution!

---

