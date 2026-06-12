---
title: "n00b apache2 alias question"
date: 2006-06-03
forum: Programming Talk
---

### Post by idn on 2006-06-03
Hi

I was wondering if someone could help me setup an alias on apache to a folder on my home directory.

The foler is at /home/idn/projects/portal/www

So when I go to [http://localhost/portal](http://localhost/portal) it goes to the directory above. I will neeed to execture php scripts in this directory.

I have googled round but havent really found a clear howto so if soeone could post step by step instructions i would  very much appreciate it :)

Thanks!

---

### Post by jgoguen on 2006-06-03
I'm assuming you already have PHP installed here?

Edit /etc/apache2/apache2.conf (orI think it's /etc/apache/httpd.conf if you're using Apache 1).  Add this line:
```
Alias /portal /home/idn/projects/portal/www
```
Now restart Apache:
```
sudo /etc/init.d/apache2 restart
```
Or /etc/init.d/apache restart if you use Apache 1.  Now, most important step.  Open a web browser and go to [http://hostname/portal](http://hostname/portal) (replace hostname with the hostname of your box, or localhost in your case it seems) and enjoy your pages.

---

### Post by David Marrs on 2006-06-03
or go to /var/www/ and set up a symbolic link to /home/idn/projects/portal/www.
```
ln -s /home/idn/projects/portal/www
```

---

### Post by jgoguen on 2006-06-03
But that creates the structure /var/www/www, meaning he would go to [http://localhost/www](http://localhost/www) instead of [http://localhost/portal](http://localhost/portal) like he said he wanted.

---

### Post by idn on 2006-06-03
[QUOTE=jgoguen]I'm assuming you already have PHP installed here?

Edit /etc/apache2/apache2.conf (orI think it's /etc/apache/httpd.conf if you're using Apache 1).  Add this line:
```
Alias /portal /home/idn/projects/portal/www
```
Now restart Apache:
```
sudo /etc/init.d/apache2 restart
```
Or /etc/init.d/apache restart if you use Apache 1.  Now, most important step.  Open a web browser and go to [http://hostname/portal](http://hostname/portal) (replace hostname with the hostname of your box, or localhost in your case it seems) and enjoy your pages.[/QUOTE]

Thanks this works great!

---

### Post by gushil on 2008-01-16
but why do if i added one slash in alias directive such as..

```
Alias /portal**/** /home/idn/projects/portal/www
```

it become unusable?

if we access files on portal apache return file not found.
any clue? (however in default /doc/ is alias with two slash, and it worked flawlessly)

---

### Post by achron on 2008-01-17
Straight from the Apache 2 docs:

The Alias directive allows documents to be stored in the local filesystem other than under the DocumentRoot. URLs with a (%-decoded) path beginning with url-path will be mapped to local files beginning with directory-path. The url-path is case-sensitive, even on case-insensitive file systems.
Example:

Alias /image /ftp/pub/image

A request for [http://myserver/image/foo.gif](http://myserver/image/foo.gif) would cause the server to return the file /ftp/pub/image/foo.gif. Only complete path segments are matched, so the above alias would not match a request for [http://myserver/imagefoo.gif](http://myserver/imagefoo.gif). For more complex matching using regular expressions, see the AliasMatch directive.

Note that if you include a trailing / on the url-path then the server will require a trailing / in order to expand the alias. That is, if you use Alias /icons/ /usr/local/apache/icons/ then the url /icons will not be aliased.

---

