---
title: "Apache Test Page shows after Website Install (configuration?)"
date: 2013-10-10
forum: New to Ubuntu
---

### Post by 3BkPKNG on 2013-10-10
I've just installed another copy of Ubuntu server 13.04 in a Virtualbox.

I ftp'd in and put drupal in /var/www/drupal. I then was able to run

```
http://(myvirtualboxIP)/drupal/install.php
```

Which installed drupal successfully.

The problem is localhost/drupal redirects to the apache test page rather than my drupal website. What piece of apache config am I missing?

---

### Post by bkline on 2013-10-10
Has apache been told that index.php is a valid default page?

---

