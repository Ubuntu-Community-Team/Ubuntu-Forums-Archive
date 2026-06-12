---
title: "PHP offline"
date: 2006-07-05
forum: Programming Talk
---

### Post by Ubuntuud on 2006-07-05
Is it possible to test my PHP scripts offline? I currently haven't got a homepage and I'm just trying somethings out. But none of my PHP scripts seem to work, so I geussed it might not be possible to run them offline. Is it? Thanks in advance!

---

### Post by echo $USER on 2006-07-05
Have you checked your php.ini file to see if register globals is active?

---

### Post by Ubuntuud on 2006-07-05
Where is that file located? (Sorry if this is a stupid question)

EDIT: Never mind, an oblivious place... Is it correct that it's called php.ini-dist?

It isn't helping btw.

Please note that even the simplest (such as: 'echo "Hello";') doesn't work.

---

### Post by Ubuntuud on 2006-07-05
And another thing: is it normal that firefox can't open .php? Mine tends to save it.

---

### Post by Note360 on 2006-07-05
Is the Mysql set up?

---

### Post by frup on 2006-07-05
Have you installed Apache and PHP from synaptic? its best to install mysql too

The php script will need to be in var/www too

---

### Post by echo $USER on 2006-07-05
[QUOTE=Ubuntuud]And another thing: is it normal that firefox can't open .php? Mine tends to save it.[/QUOTE]

If its asking you to save the .php files, then it is not set up correctly.  Use this as a guide to set up apache, php, and mysql correctly...

[http://easylinux.info/wiki/Ubuntu_dapper#Apache_HTTP_Server](http://easylinux.info/wiki/Ubuntu_dapper#Apache_HTTP_Server)

---

### Post by Ubuntuud on 2006-07-06
OK. Thanks all! I will try that guide. Thank you!

EDIT: I did the guide, but it still isn't working.

---

### Post by Laterix on 2006-07-06
[QUOTE=Ubuntuud]OK. Thanks all! I will try that guide. Thank you!

EDIT: I did the guide, but it still isn't working.[/QUOTE]
Could you list the things you have done so far? It would make helping easier.

Just in case. Here is a simple php script for testing
```

<?php
    phpinfo();
?>

```
Create a file /var/www/info.php and put that in it. Then try to open in your browser [http://localhost/info.php](http://localhost/info.php)

Could it be firewall issue?

---

### Post by indytim on 2006-07-06
Try doing a re-boot and see if Apache comes up.

IndyTim

---

### Post by Laterix on 2006-07-06
[QUOTE=indytim]Try doing a re-boot and see if Apache comes up.[/QUOTE]
Or just restart Apache server
```

sudo /etc/init.d/apache2 restart

```

---

### Post by Ubuntuud on 2006-07-06
I did the restart (found that in the guide).

Your script did work! Thanks! I didn't know that you had to put the file in that directory... But when I put my other files (my website) in there, firefox gives me a 403 (forbidden).

So I first started with a basic HTML file and run Nautilus as a superuser and clicked on that file. The file showed up as it should in firefox. Worked.

Then I tried: "http://localhost/PHP/test.htm
I made a .css stylesheet as well to test that as well. The page loads the text etc., but the stylesheet isn't used, so the page does not look like it should. Doesn't work.

Then I tried the PHP file by simply clicking on the file in a sudo nautilus. Again, it wanted to save. Doesn't work.

Then I did, in the sudo firefox: "http://localhost/PHP/index.php
This was the result:
Warning: Unknown: failed to open stream: Permission denied in Unknown on line 0

Warning: Unknown: Failed opening '/var/www/PHP/index.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in Unknown on line 0

Is this helpful?

---

### Post by Laterix on 2006-07-06
[QUOTE=Ubuntuud]I did the restart (found that in the guide).

Your script did work! Thanks! I didn't know that you had to put the file in that directory... But when I put my other files (my website) in there, firefox gives me a 403 (forbidden).
[/QUOTE]
I think your php scripts doesn't have read permissions for all. Go to **/var/www**
and execute **sudo chmod 755 -R ***. That will give read permissions to ALL for ALL files under /var/www and it's subdirs. And write permissions to the owner user.

---

### Post by frup on 2006-07-06
is it bad that i just went chown user /var/www ?

---

### Post by Ubuntuud on 2006-07-06
It's working! Thank you so much.

But there is still one more thing left, Cascading Style Sheets aren't working... Any hints on that? Thanks in advance!

---

### Post by Randomskk on 2006-07-06
Just a by the way, you HAVE to open the PHP files like:
[http://localhost/file.php](http://localhost/file.php)
Using Nautilus will directly open the file, as it does not get processed by Apache.

How are you trying to use the CSS sheet?
Try opening it directly, ie [http://localhost/style.css](http://localhost/style.css) and see if that works.

---

### Post by Ubuntuud on 2006-07-06
[QUOTE=Randomskk]Just a by the way, you HAVE to open the PHP files like:
[http://localhost/file.php](http://localhost/file.php)
Using Nautilus will directly open the file, as it does not get processed by Apache.

How are you trying to use the CSS sheet?
Try opening it directly, ie [http://localhost/style.css](http://localhost/style.css) and see if that works.[/QUOTE]

That wasn't the exact solution for the stylesheet, but it made me notice that the user rights were wrong. Thanks.

So everything is working now, I even managed to map my directory. So when I type "http://localhost/php_folder/...", it goes to "/home/pieter/HTML/PHP/..."

Thanks to everyone for all of their help. Thank you!

---

### Post by Randomskk on 2006-07-06
Quick by-the-way, but under Apache, if you have a public_html folder in your /home/username and go to [http://localhost/~username](http://localhost/~username) then it serves up that folder, so for instance:
file index.html in /home/pieter/public_html/index.html is shown when you load [http://localhost/~pieter/index.html](http://localhost/~pieter/index.html)

---

### Post by Ubuntuud on 2006-07-06
Should I create that folder myself? It isn't there yet.

---

### Post by Randomskk on 2006-07-06
Yes, you'd need to make the folder manually.

---

