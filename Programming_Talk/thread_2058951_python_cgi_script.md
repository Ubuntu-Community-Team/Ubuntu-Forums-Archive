---
title: "python cgi script"
date: 2012-09-17
forum: Programming Talk
---

### Post by micahpage on 2012-09-17
I am trying to make a python cgi script. I am not sure exactly what I am doing. I am just trying to follow along with some tutorials.
one tutorial [http://archive09.linux.com/feature/136602](http://archive09.linux.com/feature/136602)
second [http://narnia.cs.ttu.edu/drupal/node/43](http://narnia.cs.ttu.edu/drupal/node/43)

so i came here and edited this file
```
sudo nano /etc/apache2/sites-available/default

```
```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                #Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Options None
                Order allow,deny
                Allow from all
        </Directory>

```
and I changed Options to None and commented the original out

```
mkdir cgi-bin
```
and created:
/var/www/cgi-bin/example1.py
```
#!/usr/bin/env python

print "Content-type: text/html"
print
print "<html>"
print "<center>Hello, Linux.com!</center>"
print "</html>"

```

```
sudo chmod 755 example1.py
```

then restarted
```
sudo /etc/init.d/apache2 restart

```

so now am I suppose to be able to see it here? Becausse i get a 404 error.
```
http://xxx.xxx.xxx.xxx/var/www/cgi-bin/example1.py
```
at least that is what I am hearing from different sources throughout the web

---

### Post by spjackson on 2012-09-17
> **micahpage said:**
> 
```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                #Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Options None
                Order allow,deny
                Allow from all
        </Directory>

```and I changed Options to None and commented the original out

I don't understand the reason for making that change.
> 
```
mkdir cgi-bin
```and created:
/var/www/cgi-bin/example1.py
From what is in the apache config above, you should be using /usr/lib/cgi-bin and the url would be [http://xxx.xxx.xxx.xxx/cgi-bin/example1.py](http://xxx.xxx.xxx.xxx/cgi-bin/example1.py)

```

#!/usr/bin/env python 
print "Content-type: text/html"
print
print "<html>"
print "<center>Hello, Linux.com!</center>"
print "</html>"

```Why no body tag? Ah, because the tutorial doesn't have it.

```
http://xxx.xxx.xxx.xxx/var/www/cgi-bin/example1.py
```No. DocumentRoot is probably set to /var/www which means that the URL would be [http://xxx.xxx.xxx.xxx/cgi-bin/example1.py](http://xxx.xxx.xxx.xxx/cgi-bin/example1.py). However, in the apache config, cgi-bin is aliased to /usr/lib/cgi-bin, so it won't find the one in /var/www/cgi-bin/ anyway.

---

### Post by micahpage on 2012-09-17
> From what is in the apache config above, you should be using /usr/lib/cgi-bin and the url would be [http://xxx.xxx.xxx.xxx/cgi-bin/example1.py](http://xxx.xxx.xxx.xxx/cgi-bin/example1.py)

ah thank you, this worked.

So if I make it point to /var/www/cgi-bin instead it will execute that dir?

---

