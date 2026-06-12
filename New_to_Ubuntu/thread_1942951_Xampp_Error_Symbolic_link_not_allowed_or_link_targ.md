---
title: "Xampp Error: Symbolic link not allowed or link target not accessible"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by Soorin on 2012-03-18
I have installed the Xampp stack and created a symlink from home/user/Dropbox/wwwFiles to /opt/lampp/htdocs/wwwFiles, my problem is that I can't access the content of the wwwFiles folder.
In the error_log file it says: "Symbolic link not allowed or link target not accessible: /opt/lampp/htdocs/wwwFiles"
I have changed the owner and the group on both the folder to be the same nobody and nogroup, I have added the Options FollowSymLinks to the httpd.conf but with no luck, I still can't access the files in the wwwFiles.
Does somebody has a solution to this issue?!
Thank you.

---

### Post by lechien73 on 2012-03-18
Hi & welcome to the Ubuntu forums,

It could be because the owner of the symlink doesn't match the owner of the symlinked files. This is a security feature of Apache to prevent symlink attacks.

If you're sure that your server is secure, then you can add the following options to your httpd.conf file:

```
Options +FollowSymLinks -SymLinksIfOwnerMatch
```

---

### Post by Soorin on 2012-03-18
I have tried that before and the same problem.

---

### Post by Soorin on 2012-03-20
Nobody has a working solution?

---

### Post by Lars Noodén on 2012-03-20
> **Soorin said:**
> Nobody has a working solution?

XAMPP is the wrong way to go about setting up a web server for Linux.  All distros, Ubuntu included, have package managers which take care of downloading and installing.  That includes tracking version changes and security updates.  You should use the package manager to install the LAMP components.

So one solution would be to wipe /opt/lampp and start over by installing the components of your L (Linux), A (Apache/Lighttpd/nginx), M (MySQL/Postgresql), P (Perl/Python/PHP) system:
```

apt-get install openssh-server apache2 php5 mysql-server

```

Perl is built in, so that's why you don't need to add it.

With that, you'll find your web pages in a standard location (initially /var/www) and same for your other components.  

If you really want to work with XAMPP, you can still do that, but it's not the best or even a good way.

---

### Post by Soorin on 2012-03-21
Hello Lars, thank you for your suggestion.
I'm not trying to setup a production server is just for local propose.
I have fallowed your suggestion and deleted xampp.
I'm having the same problem "Symbolic link not allowed or link target not accessible: /var/www/test" 
I have the same owner and group on test folder and www folder and all files in the www folder.
Any suggestion?

---

### Post by Lars Noodén on 2012-03-21
Hmm.  What happens when you open a terminal and track the activity in the error log when you produce the error?

```

tail -f /var/log/apache2/error.log 

```

---

### Post by Soorin on 2012-03-22
I get this:
```
[Thu Mar 22 19:43:37 2012] [error] [client 127.0.0.1] Symbolic link not allowed or link target not accessible: /var/www/test

```

---

### Post by Lars Noodén on 2012-03-22
Did you make a symbolic link there?  That seems to be what might have happened.

What is the output of ls?

```

ls -lh /var/www/

```

We'll look to see if there is a link present.

---

### Post by Soorin on 2012-03-22
I have a symlink,
```
ls -lh /var/www/
lrwxrwxrwx 1 sorin sorin  24 2012-03-21 21:31 test -> /home/sorin/Dropbox/test

```

---

### Post by Lars Noodén on 2012-03-22
Does the target (/home/sorin/Dropbox/test) exist?

---

### Post by Soorin on 2012-03-22
Yes the folder exists:
 ```
ls -l /home/sorin/Dropbox/test
-rwxrwxrwx 1 sorin sorin 39 2012-03-21 21:32 index.html
```

---

### Post by Lars Noodén on 2012-03-22
I'm not able to duplicate your error on my system.  I have Apache2 set up with no modification to the configuration and it still works when I symlink to a folder within my home directory.  I've also tried changing owners of the symlink, but Apache still serves it up.  I'm not sure what you have that is different.  What changes did you make to the configuration?

---

### Post by Soorin on 2012-03-22
I only added these lines to the httpd.conf:
```
<Directory /var/www/test> 
 Options FollowSymLinks 
</Directory>
```
The httpd.conf file was empty, is this normal?

---

### Post by Soorin on 2012-03-24
I have fixed the problem.
In the httpd.conf file I have added:
```
User sorin
Group sorin
```
where sorin is the owner and the group for both the symbolic link and the target link.
Maybe this helps someone.

---

### Post by mevsme on 2012-12-15
Yes, it helped me too. But it's so non-obvious solution %) I'm angry a lot.
ps: i'm trying developing with drop box as well.

---

### Post by nikhilsheth on 2013-05-17
Soorin, thanks!
I only had to edit httpd.conf and add the lines:
User nikhil
Group nikhil
..as you advised ('nikhil' is my ubuntu user name)
And Voila! On restarting the server (I'm using XAMPP), I was able to access a "Documentaries" folder that's on my external HDD which I'd symlinked into the /opt/lampp/htdocs .
It also worked over my home's WiFi network on an Android phone.. I just had to browse to 192.168.1.2/Documentaries/
And I can now play TED Talks, which are sitting in my HDD, on the Android phone, without even having to download them :) :)

The earlier Options.. tip had no effect. This User and Group lines did the trick.

---

