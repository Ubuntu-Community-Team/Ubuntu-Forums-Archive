---
title: "Need help installing the PAM module for PHP"
date: 2009-11-04
forum: Programming Talk
---

### Post by Vunutus on 2009-11-04
The PHP project I'm working on needs to authenticate users against system user accounts. After researching, I have found a PHP module claiming to do just that. 

I downloaded the module, but unfortunately it doesn't appear to have any instructions as to how I can actually install it. I've never installed a PHP module before so I'm a little lost. The downloaded archive contains a .c and .h file so I assume it needs to be compiled first, but again, I don't know what to do. Is it possible to have a "snap-in" type module or do I need to recompile PHP altogether?

Either way, I would appreciate if someone could clear up my confusion here or provide a link explaining exactly what I need to do.

Link to module: [http://pecl.php.net/package/PAM](http://pecl.php.net/package/PAM)

---

### Post by sisco311 on 2009-11-04
The module is in the repos:
```
sudo aptitude install php5-auth-pam
```

[[noparse]http://www.dokuwiki.org/auth:pam#ubuntu[/noparse]]("http://www.dokuwiki.org/auth:pam#ubuntu")

---

### Post by Vunutus on 2009-11-04
> **sisco311 said:**
> The module is in the repos:
```
sudo aptitude install php5-auth-pam
```

[[noparse]http://www.dokuwiki.org/auth:pam#ubuntu[/noparse]]("http://www.dokuwiki.org/auth:pam#ubuntu")

Oh god I love it when things I want are apt-gettable

---

### Post by v8YKxgHe on 2009-11-04
For future reference, installing things from PECL or PEAR:

```
sudo pecl install foo; sudo pear install foo
```
You'll need the 'php5-dev' (or php-dev, I've no idea what Ubuntu uses) package first, though. If running PHP as a module to Apache, restart webserver.

---

