---
title: "[SOLVED] php5 I need to test?"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-12
How do i go about testing if my php5 is working properly. I'm running ubuntu desktop 8.10 and used synaptic package manager to install lamp. Last time i created a test.php file but i can't remember how I went about that.

---

### Post by PartisanEntity on 2008-11-12
Create a file called test.php with the following content:

```
# test.php
<?php phpinfo(); ?>
```

and place this file in */var/www/*

Then point your browser to: [http://ip-address/test.php](http://ip-address/test.php) or [http://domain-name/test.php](http://domain-name/test.php)

This should you all your configuration settings.

---

### Post by spiderbatdad on 2008-11-12
Create a file in your htdocs directory, (probably /var/www) named "test.php" Open the file with a text editor and add the line:
<?php phpinfo() ?>

Save the file...open in your browser:
[http://localhost/test.php](http://localhost/test.php)

lol partisan entity beat me to it.

---

### Post by shanep-server on 2008-11-12
i tried using the standard text editor in applications tab when i tried to save it too var/www it said i didn't have permission :/ that code u told me too type in is supposed to be put in a text editor right.

I'm having difficulty with these permission stuff but i don't wanna go missing around and lose the security root offers. If that makes any sense lol.

---

### Post by spiderbatdad on 2008-11-12
use ```
gksu nautilus
```for graphical superuser permissions. Just right click inside the directory /var/www and select create a document...then name it. Right click on the document and select "open with"...choose text editor.

---

### Post by PartisanEntity on 2008-11-12
Do this:

sudo gedit /var/www/test.php

and paste the info the text file that opens up, then save it.

---

### Post by shanep-server on 2008-11-12
alright guys thank you I think I got it now.

---

### Post by PartisanEntity on 2008-11-12
Cool, please mark your thread as solved, this helps others looking for the same topics to find working solutions quickly :)

edit: oh you did, duh :P

---

