---
title: "[SOLVED] PHP Include Directory"
date: 2008-03-09
forum: Programming Talk
---

### Post by The Titan on 2008-03-09
I'm trying to make files include-able from anywhere without the use of "../".

All my files are located in "hxxp://localhost/fw/trunk", when i do

[php]
<?php
include ("/fw/trunk/include/mysql.php"); //this file exists
?>
[/php]I assumed that it would start at root because of the "/" in front but It can't find it. and $_SERVER['DOCUMENT_ROOT']; returns "/var/www", that is definitely not what i want.

---

### Post by mike_g on 2008-03-09
AFIAK /var/www  is kind of like the default directory for the local host.

You might be able to change that somehow, but i dont know how to do that.

---

### Post by The Titan on 2008-03-09
> **mike_g said:**
> AFIAK /var/www  is kind of like the default directory for the local host.

You might be able to change that somehow, but i dont know how to do that.
i think that may be true, except this is a CMS and that could cause an issue depending on the server.

EDIT: what does "AFIAK" mean?

---

### Post by frankos44 on 2008-03-09
What's wrong with using relative paths inside php?

Dont forget you can create a symbolic link to the source folder eg.

$ ln -s /the/path/to/the/folder ./myfolder

---

### Post by The Titan on 2008-03-09
> **frankos44 said:**
> What's wrong with using relative paths inside php?

Dont forget you can create a symbolic link to the source folder eg.

$ ln -s /the/path/to/the/folder ./myfolder

generally speaking there is nothing wrong with it, but let me give you an example of something that could create an issue:

localhost/fw/trunk/class.php:
[php]
<?php
include "include/mysql.php";
?>
[/php]localhost/fw/trunk/include/someotherfile.php:
[php]
<?php
include "../class.php";
?>
[/php]someotherfile.php would break because when it includes class.php that would in turn include include/mysql.php FROM the include folder.  so it would look for include/include.php.

---

### Post by frankos44 on 2008-03-09
If I am understanding you correctly, maybe this will help. This is what I do on my server:

To include Global objects ( the objects I make available to all hosted websites on all the virtual hosts ),  I use full path names as follows:

<?php
require_once(/'var/www/common/objects/class.object1.php');
?>

In that folder I keep "template objects", "data layer objects", "html rendering objects" anything that would be universal to any websites I create.

To include website specific objects I use relative paths as follows:

<? php
require_once('../objects/class.object2.php');
?>

In here I would keep for example "quotation objects", "hit counter object", "shopping basket object" etc.

Of course I can still include the "global objects" inside the web site "specific objects" using the full pathname. One example is to include the "data layer object".

Dont forget that php has access to anything above the website home folder where as the outside world eg. browser is limited to htdocs and below. 

Here is a portion of the website folder structure that I use:

/var/www/common/objects/
/var/www/common/objects/class.object1.php

/var/www/website1/htdocs/
/var/www/website1/htdocs/images/
/var/www/website1/htdocs/index.php
/var/www/website1/objects/class.object2.php

/var/www/website2/htdocs/
/var/www/website2/htdocs/images/
/var/www/website2/htdocs/index.php
/var/www/website2/objects/class.object2.php

Hope this is helpful

---

### Post by The Titan on 2008-03-09
> **frankos44 said:**
> If I am understanding you correctly, maybe this will help. This is what I do on my server:

To include Global objects ( the objects I make available to all hosted websites on all the virtual hosts ),  I use full path names as follows:

<?php
require_once(/'var/www/common/objects/class.object1.php');
?>

In that folder I keep "template objects", "data layer objects", "html rendering objects" anything that would be universal to any websites I create.

To include website specific objects I use relative paths as follows:

<? php
require_once('../objects/class.object2.php');
?>

In here I would keep for example "quotation objects", "hit counter object", "shopping basket object" etc.

Of course I can still include the "global objects" inside the web site "specific objects" using the full pathname. One example is to include the "data layer object".

Dont forget that php has access to anything above the website home folder where as the outside world eg. browser is limited to htdocs and below. 

Here is a portion of the website folder structure that I use:

/var/www/common/objects/
/var/www/common/objects/class.object1.php

/var/www/website1/htdocs/
/var/www/website1/htdocs/images/
/var/www/website1/htdocs/index.php
/var/www/website1/objects/class.object2.php

/var/www/website2/htdocs/
/var/www/website2/htdocs/images/
/var/www/website2/htdocs/index.php
/var/www/website2/objects/class.object2.php

Hope this is helpful
i'm not sure what your trying to show me, but im just trying to avoid using, "../". I think you read a little too far into my post :lol:

EDIT: solved.  i can use $_SERVER['DOCUMENT_ROOT'] i was confused about what that superglobal actually was

---

### Post by frankos44 on 2008-03-09
> **The Titan said:**
> i'm not sure what your trying to show me, but im just trying to avoid using, "../". I think you read a little too far into my post :lol:

EDIT: solved.  i can use $_SERVER['DOCUMENT_ROOT'] i was confused about what that superglobal actually was

Sorry I have a tendency to go too deep sometimes. Its a great forum and its nice to help if I can and be helped when I need it.

---

### Post by The Titan on 2008-03-09
> **frankos44 said:**
> Sorry I have a tendency to go too deep sometimes. Its a great forum and its nice to help if I can and be helped when I need it.
Dont get me wrong man, i appreciate it.  I agree about this forum.  I have never found one as useful or as populated as this one.

---

