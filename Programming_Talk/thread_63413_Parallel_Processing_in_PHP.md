---
title: "Parallel Processing in PHP"
date: 2005-09-07
forum: Programming Talk
---

### Post by alirizwan on 2005-09-07
Hi,

I want to perform Parallel Processing in PHP. Let me try to explain my problem.
I want to open 2 files with fopen at the same time.

For Example first file takes 30 seconds and 30 seconds seond file to read in web.
and total time will be 60 seconds.
Can i read both files in 30 seconds with parallel execuation?

<?php

$handle_1 = fopen("www.domain.com/index.php", "r");
$text_1 = fread($handle_1,filesize("$handle_1"));
fclose($handle_1);

$handle_2 = fopen("www.domain.com/index.php", "r");
$text_2 = fread($handle_2,filesize("$handle_2"));
fclose($handle_2);

$text = $text_1 . $text_2;

print $text;

?>

As above code run line by line and takes much time. Is there any way that i can open both or more files Simultaneous ?
How can i execute some my code in parallel processing?


Regards,

Ali Rizwan (Web Developer)
Aztek Computers
[http://www.aztekcomputers.com](http://www.aztekcomputers.com)
..............................

---

### Post by scoon on 2005-09-08
Hey there, 

With one CPU you will not get what you are looking for.  You could try and put each file read in its own thread.  I would suggest that you set up timers around a threaded and a non threaded solution.  You will prolly find that the difference in time is not noticable.

regards, 

scoon

---

### Post by LordHunter317 on 2005-09-08
For doing I/O of this nature from the same device, it's pointless to look at threading or any other solution.  

Not to mention that if this is going to come to run on a webserver, you're likely not going to be capable.

---

### Post by scoon on 2005-09-08
Hey there, 

That is ultimately correct, but I thought it wise to offer an idea to chew on.

regards, 

scoon

---

