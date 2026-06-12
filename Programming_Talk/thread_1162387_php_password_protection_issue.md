---
title: "php password protection issue"
date: 2009-05-17
forum: Programming Talk
---

### Post by vitotol on 2009-05-17
hello guys, i have a problem and i need some help...

i have a php script that creates an image which shows some info taken from a database.
to display the image to the browser through the url, the script must have read permissions so the password can be read.

how can i protect the password, i tried to get it from an included php file but it must be readable too. what should i do:confused:???

---

### Post by s.fox on 2009-05-17
Hi,

Any password scripts that I include are never web facing.  Set permissions like how you need and then

You could just go something like 

```

<?php
include ("../../../../password.php");
?>
 
```

Hope this gives you some ideas

-Ash R

---

### Post by vitotol on 2009-05-17
thanx for your reply but i need to protect the password from other users too. this script is for a server.

---

