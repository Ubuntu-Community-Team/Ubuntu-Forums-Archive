---
title: "include_once not working"
date: 2013-03-11
forum: Programming Talk
---

### Post by criscalleo on 2013-03-11
Hello all,
I have performed a LAMP installation.
All working right, except include function in PHP.

On index.php i have 2 include:
include_once "../config.php";
include_once "../header.php";

When i open this page nothing is included.

Any suggestion to solve?

TKS

---

### Post by SeijiSensei on 2013-03-11
See if any errors are logged in /var/log/apache2/error.log. You'll need to have root privileges via sudo to see this file.  As a guess ../config.php probably isn't in the location you think it is.  Try using full paths.

```
include_once "/path/to/config.php";
```

---

### Post by greenpeace on 2013-03-13
Hey, 

Just to add to SeijiSensei's answer above, your script is looking for the files in the *parent* directory of the index.php file ... that's what the "../" means at the beginning of the file path.

So if your index.php file is here:  **/var/www/site/index.php** then it will be looking for the two files here:
[LIST]
[*]/var/www/header.php
[*]/var/www/config.php
[/LIST]
and I guess it's not finding them there.

Good luck!
Gp

---

