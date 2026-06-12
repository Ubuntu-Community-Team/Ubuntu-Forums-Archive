---
title: "[SOLVED] [PHP] URL Scheme"
date: 2008-05-18
forum: Programming Talk
---

### Post by -grubby on 2008-05-18
I'm not exactly sure how to describe this problem.. I'm trying to make the URL scheme change from something like "http://site.com/about.php" To something like "http://site.com/index.php?p=about". I tried using some if statements using "isset". Didn't seem to work out. Any Ideas?

---

### Post by LaRoza on 2008-05-18
My site just uses a switch statement. The default case will catch it if the variable in the URI doesn't have a value.

---

### Post by -grubby on 2008-05-18
Well, I figured it out. Here's the PHP code I'm using (sample code..not the code I'd actually use):

[php]
<?php
    $p = $_GET['page']; 
   
    switch($p)
    {
        case page1:
	    include('error_log');
            break;
	case page2:
	    include('robots.txt');
	    break;
        default:
   	    echo 'hi!';
            break;
    }

?>
[/php]

---

