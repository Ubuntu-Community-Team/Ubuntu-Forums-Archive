---
title: "Where to store php programs on Ubuntu 18.04"
date: 2019-05-24
forum: Programming Talk
---

### Post by zak100 on 2019-05-24
Hi,
 I am trying to run php programs. I have installed nginx web server. When i use whereis command it shows me different paths for nginx

 
 
 $ whereis nginx
 nginx: /usr/sbin/nginx /usr/lib/nginx /etc/nginx /usr/share/nginx /usr/share/man/man8/nginx.8.gz
 
 
 
 
 Kindly guide me the path where should I store the php programs.
 
 
 Zulfi.

---

### Post by &amp;KyT$0P# on 2019-05-24
Check your nginx config in [FONT=Courier New]/etc/nginx/sites-enabled[/FONT] , look for the "root" directive.

---

### Post by zak100 on 2019-06-07
Hi,
I got following:
/etc/nginx/sites-enabled$ ls
default

And when I launched "default" using vi, I got:
root /var/www/html;

What does the above mean?
Zulfi.

---

### Post by TheFu on 2019-06-07
[https://askubuntu.com/questions/134666/what-is-the-easiest-way-to-enable-php-on-nginx](https://askubuntu.com/questions/134666/what-is-the-easiest-way-to-enable-php-on-nginx)
nginx doesn't handle php code directly. It requires the fastcgi module.  
All the steps to configure a web server like nginx are well beyond what I'd post in these forums.  Look for a guide. Probably want to look for a guide that is for php + nginx.  If you plan to use a DBMS too, then look for an all-in-one guide, since that would be a *LEMP* stack. Search for that.

BTW, **whereis** doesn't do what you think it does:```

NAME
       whereis  -  locate the binary, source, and manual page files for a command
...
```
That's the summary in the manpage.  There is a manpage for almost all commands.  Because nginx is so very complex, more than the manpage is necessary to make use of it and definitely to configure it.

sites-enabled/ and sites-available/ are common directories in webserver configurations.  They are used to manage which virtual websites are ... available vs .... enabled.  Normally, a symbolic link is used to enable a site in the "available" directory over into the "enabled".  There are lots of little details like that in configuring every webserver.  Config options, added modules, conditional modules, sites, SSL vs non-SSL and lots of techniques to secure your website from bad-actors trying to break it and gain direct access to your server so they can have it do what they want instead.

---

### Post by TheFu on 2019-06-09
> **zak100 said:**
> Hi,
I got following:
/etc/nginx/sites-enabled$ ls
default

And when I launched "default" using vi, I got:
root /var/www/html;

What does the above mean?
Zulfi.

"default" is the name of the default nginx website configuration file. It is actually a symbolic link to the real file in ../sites-available/default file.  By adding different website configuration files to the "sites-available/" directory, you can work on multiple virtual websites on the same system, and enable them one at time to ensure they work and don't conflict with any others.  After that testing, you can enable them all, see that they all work, and be happy.

The nginx website configs are complex, but they can be trivial for a static webpage.

"root" says this is the top level for a website.

/var/www/html says that is the directory location on the local computer for the default website. If nginx is running, it will look for an index.html file to be returned to a requesting client in that directory.  Point your web broser at the IP address of the system - you should see the default nginx html file.  It should say something like:

**Welcome to nginx!**

That's a bunch of words for a very simple idea.

---

### Post by xavierbaez on 2019-06-16
```
$ which -a nginx
```

---

### Post by TheFu on 2019-06-16
> **xavierbaez said:**
> ```
$ which -a nginx
```

And this only returns the binary daemon location, not where the default webapp might belong.
```
$ which -a nginx
/usr/sbin/nginx
```
That's it. Nothing more.

---

### Post by xavierbaez on 2019-06-17
> **TheFu said:**
> And this only returns the binary daemon location, not where the default webapp might belong.
```
$ which -a nginx
/usr/sbin/nginx
```
That's it. Nothing more.

```
dpkg -L nginx-common
```

returns all the files, I believe it's this folder:
```
/var/www/html
```

---

### Post by TheFu on 2019-06-17
Using the default location is probably not a good idea if the OP plans to have multiple virtual websites on the same server.  Where any webapp is placed is completely up to the webmaster/admin.  I haven't used the default location on a web server in about 25 yrs.

The OP hasn't been back in a week. Good luck.

---

