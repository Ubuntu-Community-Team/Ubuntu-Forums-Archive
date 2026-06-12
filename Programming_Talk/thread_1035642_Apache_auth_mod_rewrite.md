---
title: "Apache auth mod_rewrite"
date: 2009-01-09
forum: Programming Talk
---

### Post by openjoel on 2009-01-09
Hello,
i have a rewrite rule that look like this:
RewriteRule ^@[a-z]+/([A-Za-z0-9-]+)$ index.cgi [L]
witch produces links that look like this,
[http://foo.bar/wiki/@edit/page](http://foo.bar/wiki/@edit/page)
or [http://foo.bar/wiki/@meta/data](http://foo.bar/wiki/@meta/data)

The thing is that I want to protect links that look like the first one but not the second one. And I want to protect it by using .htacces (mod_auth)

I have no clue of how to do that. The only think I have manage to come up with is in httpd.conf:
```
<Directory /var/www/wiki/@edit>
       AuthName "Edit this page?"
       AuthType Basic
       AuthBasicProvider file
       AuthUserFile /var/passwd
       Require valid-user
</Directory>
```
But I get nothing!

Thanks for your time, Please help me!

---

### Post by slavik on 2009-01-10
have you tried reloading apache and clearing browser cache? also try using something that is not firefox ... I've had issues with firefox caching things.

---

### Post by openjoel on 2009-01-10
> **slavik said:**
> have you tried reloading apache and clearing browser cache? also try using something that is not firefox ... I've had issues with firefox caching things.

Yes I have. Still no respons!

---

