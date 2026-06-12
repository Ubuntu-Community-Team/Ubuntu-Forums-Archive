---
title: "Changing headers with php error"
date: 2011-11-16
forum: Programming Talk
---

### Post by Zigon on 2011-11-16
I have a button where the user can download a pdf file, instead of opening in their browser. This works on my local server but when when hosted on Yahoo, I receive "500 - Internal Server Error".

index.php:
[PHP]
<a href="../download.php"><img src="../site_images/pdf_icon.png"></a>
[/PHP]

download.php:
[PHP]
header('Content-disposition: attachment; filename=n_catalog.pdf');
header('Content-type: application/pdf');
readfile('catalog.pdf');
[/PHP]

EDIT: Fixed it by updating the PHP version on the server.

---

### Post by Bachstelze on 2011-11-16
You forgot the PHP openoing tag. ;)

[php]<?php
header('Content-disposition: attachment; filename=n_catalog.pdf');
header('Content-type: application/pdf');
readfile('catalog.pdf');  [/php]

*EDIT:* Though if it works on your local server, I guess that's not the problem... Yahoo probably just doesn't let you do that.

---

### Post by Zigon on 2011-11-16
I just forgot to copy them in, they're in there though lol thanks. Ya I guess I'll go contact them.

---

