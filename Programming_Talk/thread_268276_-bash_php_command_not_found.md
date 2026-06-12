---
title: "-bash: php: command not found"
date: 2006-09-29
forum: Programming Talk
---

### Post by McHenry on 2006-09-29
I have a script that I run from the command line on Centos simply by typing:
php script.php

When I tried this with Ubuntu I reveived:
-bash: php: command not found

I checked the php docs and it states to run php -v to check your version for the php CLI module:
[http://www.php.net/manual/en/features.commandline.php](http://www.php.net/manual/en/features.commandline.php)

However event this doesn't work...
I am guessing the php executable is not located in the path but have no idea how to rectify this...

Thanks

---

### Post by scxtt on 2006-09-29
do you have the equivalent of **php5-cli** installed?

**sudo aptitude install php5-cli**

---

### Post by McHenry on 2006-09-29
Now I do... :)

On Centos I didn't actually use a cli module the only diff I could see is that the std module output the headers however this was not a problem for me.

now when I enter php -v I am presentled with:
PHP 5.1.2 (cli) (built: Sep  6 2006 22:04:21)
Copyright (c) 1997-2006 The PHP Group
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies

Does this look right ?

Thanks

---

### Post by scxtt on 2006-09-30
looks good to me, i haven't installed php5-cli this time (but i do use php for websites) so i can't check ... but if you can do **$:> php myPHP.php** and get output, you're all set :)

---

