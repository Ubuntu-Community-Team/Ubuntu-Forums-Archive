---
title: "Configuring mod_rewrite to not change address bar"
date: 2008-04-17
forum: Programming Talk
---

### Post by MicahCarrick on 2008-04-17
When I use mod_rewrite on my various hosts or servers, the rewrite rules are unknown to the user. However, when I use mod_rewrite on my local test environment (ubuntu 7.10) it rewrite the URL correctly but DOES display it in the address bar.

RewriteRule ^(.*)/$ http://localhost/qs/index.php?category_slug=$1

So if I type in [http://localhost/qs/test/](http://localhost/qs/test/) it changes it in the address bar to [http://localhost/qs/index.php?category_slug=test](http://localhost/qs/index.php?category_slug=test)

I don't want it to do that. Help?

---

### Post by mssever on 2008-04-17
> **MicahCarrick said:**
> When I use mod_rewrite on my various hosts or servers, the rewrite rules are unknown to the user. However, when I use mod_rewrite on my local test environment (ubuntu 7.10) it rewrite the URL correctly but DOES display it in the address bar.

RewriteRule ^(.*)/$ http://localhost/qs/index.php?category_slug=$1

So if I type in [http://localhost/qs/test/](http://localhost/qs/test/) it changes it in the address bar to [http://localhost/qs/index.php?category_slug=test](http://localhost/qs/index.php?category_slug=test)

I don't want it to do that. Help?
If you put http:// in the rewrite target, mod_rewrite does an external redirect. Use a relative path.

---

### Post by MicahCarrick on 2008-04-17
Perfect. Thank you much!

---

