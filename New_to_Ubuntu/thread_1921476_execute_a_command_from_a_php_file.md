---
title: "execute a command from a php file"
date: 2012-02-06
forum: New to Ubuntu
---

### Post by herbert tamayo on 2012-02-06
hi, i need to execute this line from my php file:

[PHP]
$xcurdate=shell_exec('date');
[/PHP]

the file permissions are:
```

-rwxr-xr-x

```

but the var is not filled, I think it's a file permissions issue, my questions is:

what permissions should have this file to work this line?

regards

---

### Post by Dave_L on 2012-02-06
I just tried that, and it worked.

Contents of /tmp/1.php:

```
<?php
$xcurdate=shell_exec('date');
var_dump('xcurdate', $xcurdate);
?>
```

> $ php /tmp/1.php
string(8) "xcurdate"
string(29) "Mon Feb  6 20:48:13 EST 2012
"

File permissions of /tmp/1.php are 644.

---

