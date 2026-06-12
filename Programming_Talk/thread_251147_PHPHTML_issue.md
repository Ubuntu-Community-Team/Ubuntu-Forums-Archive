---
title: "PHP/HTML? issue"
date: 2006-09-05
forum: Programming Talk
---

### Post by misterE0 on 2006-09-05
this is probably a very simple/stupid one, but i've just started playing around with php.  I setup my file server to also be a lampp server.  Playing around with some files, I basically have a directory tree like this:

root:
-myfolder
---index.php
-imagefolder
-core.css
-common.htm
-index.php

so there's an index.php in the root folder and in the myfolder folder.  common.htm has the header information for my website ([www.borgish.com](www.borgish.com) if anyone wants to see...wip).  index.php from both the root dir and the myfolder dir references common.htm via "<?php require 'common.php';?>".

common.htm refers to core.css and a few images in the imagefolder folder.  Now, on my LOCAL lampp server if i have those referenced as "/core.css" and "/imagefolder/image.png" it will not find the files, however, when I upload them to my webserver, it will.  

So basically the issue is with relative path names.  Is this some compatibility issue between ISS vs Apache, or is there something i'm not seeing?  Appologies for the winded post.

---

### Post by Miademora on 2006-09-05
In your example you are not using relative paths for /core.css and /imagefolder/image.png. Those are fixed paths with the apache documentroot.

To solve your problem you should check your apache error log file. It includes lines like the following

```
[error] [client 65.54.188.143] File does not exist: /srv/www/robots.txt
```

Check if the core.css is in the right location or adjust your path from a fixed to a relative one like imagefolder/image.png.

---

### Post by ifokkema on 2006-09-07
What I always do and what may help you out, is writing down the relative path to the root directory in every *.php file (excl. the includes). So:

[PHP]<?php
define('ROOT_PATH', './');
?>[/PHP]
for the /index.php file, and
[PHP]<?php
define('ROOT_PATH', '../');
?>[/PHP]
for the myfolder/index.php file. **Please note the change from ./ to ../**

Then use:
[PHP]require ROOT_PATH . 'common.php';[/PHP]
and you'll always get the path right. However, the 'common' file must become a .php file, so that you can use:
```
<LINK rel="stylesheet" type="text/css" href="<?php echo ROOT_PATH; ?>core.css">
```

Now, everything will work regardless if it's in / or in /my_website or /~myusername/mywebsite or whatever.

HTH

---

### Post by misterE0 on 2006-09-07
Thanks everyone for your help...that last one certainly sounds like a winner.  I think i'm gonna set up locahost subdomains, so that should fix the issue as well.  Thanks again.

---

