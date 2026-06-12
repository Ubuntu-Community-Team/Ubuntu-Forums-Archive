---
title: "Need to remove PHP 5.5 or downgrade (already installed phpbrew)"
date: 2015-03-11
forum: New to Ubuntu
---

### Post by numan2 on 2015-03-11
Hi All,

I'm setting up a ubuntu 14.04 server to run SugarCRM.  I have installed Apache 2.4, mySQL 5.5, and needed a certain version of PHP.  There's currently two versions on PHP on the box.  I need to run 5.4 but PHP 5.5.9 is shown when I do php -v.  To fix this problem I went ahead and installed phpbrew with php version 5.4.38.  Whenever the box is rebooted is shows version 5.5.9.  I have to run the command 'phpbrew switch php-5.4.38 to change the version.

root@koa:/# php -v
PHP 5.4.38 (cli) (built: Mar  5 2015 08:37:45)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.4.0, Copyright (c) 1998-2014 Zend Technologies
root@koa:/# which php
/root/.phpbrew/php/php-5.4.38/bin/php
root@koa:/#

Before I can even install Sugar I fail at the system check level (5.5 is not supported).  It's telling me that I am running php 5.5.9-1ubuntu4.6 even though php -v shows 5.4.38.  
What are my options?  I think the next step for me is to remove php 5.5.  What do you guys think?  Also, If I need to remove is there an easy way to do this?

Thanks!

---

### Post by cariboo on 2015-03-23
Did you try:

```
sudo apt-get purge php5
```

---

