---
title: "How to add extensions to PHP 5 running as an Apache 2 module"
date: 2007-11-04
forum: Programming Talk
---

### Post by killthelight on 2007-11-04
I had a problem with installing extensions for PHP5 running on Ubuntu server 6.10 with Apache2... found the solution (and wrote about it [here]("http://www.joshsharp.com.au/blog/view/how_to_add_extensions_to_php_5_running_as_an_apache2_module")) and thought I should share the knowledge, as a lot of people are getting told the wrong information.

If you need to install extra extensions for PHP like GD, curl... you do **not** have to recompile PHP, add handlers into Apache's conf files, etc etc... you can **download the extensions from the repository** and they will just work.

Search for "php5" in synaptic or use (for example):

```
sudo apt-get install php5-gd
```

give Apache a force-reload and you're all set. Much easier than the other solutions I found.

Hope this helps someone.

---

### Post by jim@wgp on 2008-12-22
Many thanks for this help, it was just what I needed :)

---

### Post by Reiger on 2008-12-22
Doesn't apt take care of the reload out of the box?

---

### Post by drubin on 2008-12-22
> **Reiger said:**
> Doesn't apt take care of the reload out of the box?

Hope not.. 

I like to re-load my configs/applications on my own time now straight after install

---

