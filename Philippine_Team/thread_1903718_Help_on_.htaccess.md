---
title: "Help on .htaccess"
date: 2012-01-03
forum: Philippine Team
---

### Post by kenweill on 2012-01-03
Need help on setting up .htaccess

My subpages doesn't work without " / " at their end.

example:
```
www.domain.com/subpage1
``` (gets an error)
while
```
www.domain.com/subpage1/
``` (works normal)

There must be a way to redirect (via htaccess) all "subpages" to "subpages/" but  I just don't know how.

Anyone knows how to do it?
Thanks in advance. :)

---

### Post by Lars Noodén on 2012-01-03
Which web server are you using, Apache, Lighttpd, nginx or another?

---

### Post by kenweill on 2012-01-03
Apache.
I'm on a web host (hostgator) and they're using CentOS with Apache.
I just need a solution via .htaccess

---

### Post by kenweill on 2012-01-05
Tried this one and it works on subpage1. Means, I have to enter a new entry for subpage2, subpage3 and so on.

```
RewriteCond %{REQUEST_URI} (.*)/subpage1?$
RewriteRule ^(.*)$ %1/subpage1/ [NE,R,L]
```

I tried:
```
RewriteCond %{REQUEST_URI} (.*)/*?$
RewriteRule ^(.*)$ %1/*/ [NE,R,L]
```
but it gives an error.

What else can I do to avoid making a htaccess entry for each subpages?

---

