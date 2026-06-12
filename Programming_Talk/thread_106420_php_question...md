---
title: "php question.."
date: 2005-12-20
forum: Programming Talk
---

### Post by Swab on 2005-12-20
I need to run a php script from the command line and want to be able to pass variables when calling the program... is this possible?  Thanks for your time.

---

### Post by Virak on 2005-12-20
Install php4-cli/php5-cli (whatever matches the version of PHP you're using. I haven't tried php4 (because php5 is better :P) but it should work the same) with synaptic/apt-get/whatever, and read [this]("http://ca.php.net/manual/en/features.commandline.php").

---

### Post by simon w on 2005-12-21
Once phpX-cli is install:

```
echo "<?php print_r($argv); ?>" > test.php
```
```
php -q test.php arg1 arg2 arg3
```

---

### Post by Swab on 2005-12-21
Thanks for the help guys... everything is working great!

---

