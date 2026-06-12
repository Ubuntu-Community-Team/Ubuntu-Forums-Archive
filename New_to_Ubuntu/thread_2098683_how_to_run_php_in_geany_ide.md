---
title: "how to run php in geany ide?"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by pushkar100 on 2012-12-27
hello everyone :) im a complete beginner to php and i heard that geany is one of the best lightweight ides.

i have created an index.php which prints hello world. but i have no idea how to compile it and get it running ! if anybody can help me with i'd be very grateful.

im using easyphp 12.1 with php 5.4.8 (on windows 7) ... if that helps :)

also, do i need to configure any settings ? 

thank you in advance :)!

---

### Post by Merrattic on 2012-12-27
1. Have you got a web server running?
2. Have you tested your php is working by running a file called info.php containing ```

  <?php phpinfo(); ?>
```[COLOR=#000000][COLOR=#0000BB][COLOR=Black] from your web servers root directory?
3. You will need to place your geany created file in the web server's root directory for php to pick it up.[/COLOR]
[/COLOR] [/COLOR]

---

### Post by pushkar100 on 2012-12-27
yes ive got apache and mysql running on my comp(easyphp)
and yes ive created and tested the file containing phpinfo()
i have set the alias of the web server to a folder called "php projects". it works when i open it from localhost. but when trying to run from geany i get an error sayin php is not recognised command etc... something abt batch file etc.

should i place the index.php file inside C:\Program Files\EasyPHP-12.1?

---

### Post by Merrattic on 2012-12-28
Not quite sure what geany is doing, seems it tries to run just the php, in a terminal.

My normal workflow is on remote servers, so I tend to have a browser window open to the page in question, and access the file with ftp using filezilla, set to edit files in geany. On saving changes to the file in geany, filezilla then offers to re-upload the file to the server. Once done, I can refresh the browser window to see the changes. Sounds a bit long winded, but only takes a couple of clicks. I would probably work like this if I have a local web server in place.

---

