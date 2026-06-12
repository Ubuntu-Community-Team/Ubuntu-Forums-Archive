---
title: "getting php variables to display in an HTML document"
date: 2008-01-21
forum: Programming Talk
---

### Post by mtn_man on 2008-01-21
I seem to be having a problem getting my php vars to show up in my html files.

I know that php is enabled and running on my server as a module of apache and have successfully gotten the famous phpinfo() method to run and display in a browser, but I cannot get even the simplest of output to display when I try to embed some php into an HTML file.

Here is what I have tried:

<?php 
        echo rand();
?>

yields nothing...

This also is not working:

<?php 

   $num = 10;
?>

in HTML file:

   <p>This is a number from php: <?php echo $num; ?> </p>

I am not sure if I just have my syntax messed up or if I am missing some php/apache config directive or what?

Thanks in advance for any help you might have to offer,

mtn_man

---

### Post by stump138 on 2008-01-21
first thing to try would be a phpinfo to see if your php apache is setup correctly.  Create a file called "phpinfo.php" and put the following into it.

[PHP]<?php
phpinfo();
?>[/PHP]

upload it to your webserver and try the url

[http://webserver_address/phpinfo.php](http://webserver_address/phpinfo.php)

If your php/apache setup is good, you should get an information sheet.

---

### Post by fluteflute on 2008-01-21
The first certainly works fine for me. 

Are your second two in the same document? If not it will not work.

---

### Post by mtn_man on 2008-01-21
Yes they are in the same document...is there any issue trying to display the results within a div tag?

---

### Post by stump138 on 2008-01-21
shouldn't be an issue if you are trying to place it inside of a <div>  You can try and see if your php is just working properly
[PHP]<?php
$num = 10;
echo $num;
?>[/PHP]

---

### Post by mtn_man on 2008-01-21
OK i figured it out...I needed to modify apache's conf file to allow php in html files...

Thanks all for the help!

mtn_man

---

