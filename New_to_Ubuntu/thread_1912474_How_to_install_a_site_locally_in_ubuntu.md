---
title: "How to install a site locally in ubuntu"
date: 2012-01-20
forum: New to Ubuntu
---

### Post by num85 on 2012-01-20
Hi,
I am trying to install a site locally on my computer which is running Ubuntu 11.10. 
I've installed apache, php, mysql and phpmyadmin to my machine and everything is working fine. 
I can't however figure out how to load the sites files which I have stored locally. 
When I point to localhost/filename I get a 404 message - does anyone know what i'm doing wrong?

How do I navigate to the sites installation files which I have stored locally in my download folder? 

Any help much appreciated.

---

### Post by CharlesA on 2012-01-20
Did you do any configuration of Apache? By default it serves files in /var/www/. If there are no files there it will give you a 404.

You'd have to move/copy the install files to /var/www to access them.

The other option is to change the DocumentRoot to point somewhere else (which is what I did on my web dev box), that way you don't have to mess with permissions.

[http://serverfault.com/questions/135993/how-do-i-change-the-document-root-of-a-linux-apache-server](http://serverfault.com/questions/135993/how-do-i-change-the-document-root-of-a-linux-apache-server)

---

### Post by num85 on 2012-01-20
Thanks for replying, I tried changing the value for DocumentRoot but I get a 404 - not too sure what I'm doing wrong as I am specifying the right file-path but unfortunately no luck. 
As I'm a newbie to Ubuntu can you explain how I can move files into the var/www folder as I hope that would work instead.

---

### Post by CharlesA on 2012-01-20
> **num85 said:**
> Thanks for replying, I tried changing the value for DocumentRoot but I get a 404 - not too sure what I'm doing wrong as I am specifying the right file-path but unfortunately no luck. 
As I'm a newbie to Ubuntu can you explain how I can move files into the var/www folder as I hope that would work instead.

What did you change the DocumentRoot to? Did you restart apache?

```
sudo service apache2 restart
```

You can move files to /var/www/ by using this:

```
sudo mv /path/to/files /var/www/
```

---

### Post by num85 on 2012-01-20
I changed the document root to home/user/downloads/openpublish but that didn't work but I've managed to move the files so all is working now - thanks for your help! :D

---

### Post by CharlesA on 2012-01-20
Ah. The path should probably have been /home/user/Downloads/openpublish

Linux is case sensitive and it needs the full path.

In any case, glad you got it working, so you mark the thread as [SOLVED] from the thread tools menu.

---

