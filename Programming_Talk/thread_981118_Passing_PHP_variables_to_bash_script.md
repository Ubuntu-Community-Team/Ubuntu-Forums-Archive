---
title: "Passing PHP variables to bash script"
date: 2008-11-13
forum: Programming Talk
---

### Post by craigp on 2008-11-13
I am trying to pass variables from php to bash and im not sure how to get this to work. this is what i am trying:

PHP:
```
<?php
echo '<pre>';
$var1="hello";
$var2="joe";
putenv("VAR1=$var1");
$last_line = system('/home/www/public_html/domain.com/script/ls $var1 $var2', $retval);
echo '
</pre>
<hr />Last line of the output: ' . $last_line . '
<hr />Return value: ' . $retval;
?>
```

BASH:
```
#!/bin/bash

ls
sudo mkdir test
sudo chown -R www-data:www-data /home/www/public_html/domain.com/script/test
echo -e "var1: $1, var2: $1"
```

but nothing seems to get passed to bash. I want to be able to do this to create new folders, give ownership and permission changes to those folders, and later create new virtualhosts with a php interface.

Cheers

---

### Post by craigp on 2008-11-13
nevermind i figured it out.. i had to use a diffent type of quotes

$last_line = system("/home/www/public_html/domain.com/script/ls $var1 $var2", $retval);

i'll leave it up for anyone else

---

### Post by drubin on 2008-11-13
> **craigp said:**
> nevermind i figured it out.. i had to use a diffent type of quotes

$last_line = system("/home/www/public_html/domain.com/script/ls $var1 $var2", $retval);

i'll leave it up for anyone else

Just so you and any one else understands. Double quotes are parsed as if their contents were php.

Yours could have been written with single quotes using concat.
system('/home/www/public_html/domain.com/script/ls '.$var1.' '.$var2, $retval);
[http://www.php.net/types.string](http://www.php.net/types.string)

---

### Post by craigp on 2008-11-13
ahh i'll edit that.. thanks

---

