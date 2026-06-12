---
title: "Mod_rewrite QUERY_STRING to directory?"
date: 2011-04-02
forum: Programming Talk
---

### Post by DarkBabylon on 2011-04-02
So I have a simple mod_rewrite problem:

I want this:
mydomain.com/index.php?p=article&id=24sfhjs2378dhs

to be:
mydomain.com/article/24sfhjs2378dhs


Currently I'm using:
```

# General Stuff
Options +FollowSymLinks
RewriteEngine On
RewriteBase /

#Domain removal of www.
RewriteCond %{HTTP_HOST} ^www\.(([a-z0-9_]+\.)?thebabylontimes\.com)$ [NC]  
RewriteRule .? http://%1%{REQUEST_URI} [R=301,L]

#Redirection (which is working btw) for a couple pages
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule ^home /index.php?p=home [L]
RewriteRule ^music /index.php?p=music [L]
RewriteRule ^tech /index.php?p=tech [L]

```


Thanks so much, this is very urgent.
Cheers,
--
Nick.

---

### Post by nshiell on 2011-04-03
What is the .htaccess doing at present?

---

