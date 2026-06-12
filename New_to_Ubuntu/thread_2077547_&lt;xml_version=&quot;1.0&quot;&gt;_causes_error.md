---
title: "&lt;?xml version=&quot;1.0&quot;?&gt; causes error"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by Frank P on 2012-10-28
Ubuntu 12.04 LTS server Apache 2 PHP5.3
 
If the first line in an pure html file is
<?xml version="1.0"?> 
runs fine
 
If it's first line in a php file - containing the same html, I get a 500 error. 
If I remove that line the PHP runs
 
Where can I find the reason for this
 
Thanks
 
Frank

---

### Post by Azdour on 2012-10-29
Hi,

It's probably because PHP is not configured for viewing short tags like the single ? character in:

> <?xml version="1.0"?> 

From the PHP manual:

> 
 short_open_tag boolean

    Tells PHP whether the short form (<? ?>) of PHP's open tag should be allowed. If you want to use PHP in combination with XML, you can disable this option in order to use <?xml ?> inline. Otherwise, you can print it with PHP, for example: <?php echo '<?xml version="1.0"?>'; ?>. Also, if disabled, you must use the long form of the PHP open tag (<?php ?>). 

---

### Post by Frank P on 2012-10-29
That line is put in by my PHP IDE when it creates a new HTML page.
Since the PHP docs recommend not using short tags I guess I'll just remove it - unless there is some reason I need it ?
 
BTW is it ok to ask ubuntu/apache questions in this forum or should I use an apache forum ?
 
Thanks
 
Frank

---

### Post by Azdour on 2012-10-29
Hi,

Maybe the Programming Talk sub-forum is a better place to ask these kind of questions:

[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Frank P on 2012-10-29
Okay,
Thanks
Frank
 
how do I mark this solved?

---

### Post by Azdour on 2012-10-29
Hi,

Up near the top of the page, to the right you should find 'Thread Tools'. Click on this and you should be able to mark the thread Solved.

---

