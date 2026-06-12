---
title: "[PHP] Question about scripts and locations."
date: 2007-12-09
forum: Programming Talk
---

### Post by sajro on 2007-12-09
I am trying to make a script I can include on all my pages. However, with nowhere to test them (server's not up yet) I've run into a small roadblock. I just need to know:

[B]
Short, no examples:[/B] Are links from a script included in another relative to its location or the location of the script including it?[B]

Long version, with examples:[/B] If foo.php is located at */var/www/lorem/foo.php* and it includes a script at */var/www/include_me.php*, would include_me.php's ```
<a href="/ipsum/content/php">
``` lead to */var/www/ipsum/content.php* (the intended) or */var/www/lorem/ipsum/content.php* (because of foo.php's location)? 

Thanks in advance for any help!
- Sajro

---

### Post by geirha on 2007-12-09
This might be a bit confusing :)

The html anchor in your example will use /var/www as it's root. So
[php]<a href="/ipsum/content/php">[/php] will link to **/var/www/ipsum/content/php**

PHP however, will use the filesystem's root as root, so
[php]<?php include("/ipsum/content/php"); ?>[/php] will refer to **/ipsum/content/php**

To include /var/www/include_me.php, you would use
[php]<?php include("../include_me.php"); ?>[/php]

---

### Post by sajro on 2007-12-09
> **geirha said:**
> This might be a bit confusing :)

The html anchor in your example will use /var/www as it's root. So
[php]<a href="/ipsum/content/php">[/php] will link to **/var/www/ipsum/content/php**

PHP however, will use the filesystem's root as root, so
[php]<?php include("/ipsum/content/php"); ?>[/php] will refer to **/ipsum/content/php**

To include /var/www/include_me.php, you would use
[php]<?php include("../include_me.php"); ?>[/php]

So
[php]<?php include("../include_me.php"); ?>[/php] in /var/www/lorem/foobar.php would include /var/www/include_me.php and /var/www/include.php's link to /var/www/ipsum/content.php would in fact go to the intended destination and not /var/www/lorem/ipsum/content.php (which is nonexistent)?

---

