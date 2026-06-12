---
title: "Ubuntu + Apache2 + PHP7.4 (PHP not execute when files not own by root)"
date: 2020-09-24
forum: New to Ubuntu
---

### Post by kiratiprogramming on 2020-09-24
Thank you so much for dropping by :)

I am very new to Linux and decided to start my Linux journey with Ubuntu.


To get to the point, I am planning to use Ubuntu as a web server.

Therefore, I installed Apache2 and PHP7.4 together.



The default folder for the web is /var/www

I first try to test whether PHP can run properly by created a file which contain 

<?php phpinfo();?>

by using the command # sudo nano /var/www/info.php

As a result, I file "info.php" was created under user=root group=root

and the PHP was executed and shown properly on the web browser at 192.168.xx.xx/info.php


However, problems occurred when I journeyed further...

1. When I uploaded a new PHP file (Test.php)(just to show "Hello world") to the web folder via Filezilla, 
the files I uploaded was shown to be owned by my username and my group, not by root.
and PHP won't executed and shown as plain codes on the web browser.

Therefore, I tried to fix it by changing both user and group of the file to root,
using the command # sudo chown root:root /var/www/Test.php
then PHP executed properly on the web browser.

-----------------------------------------------

2. I then tried to change the home directory of the web from (/var/www) to (/home/myusername/www).
The HTML pages was shown correctly, but PHP was not working and shown as plain codes.
I though I could fix the problem by just changing user and group of the PHP files to root.
Unfortunately, this time it did not work...

I have been searching all over the net on how to fix this issue, but none worked....

Finally, I changed the home directory back to /var/www/ and things are now back to normal.

But that's is not what it should be, right? I suppose to be able to do more with it.

-----------------------------------------------

So it comes to 2 problems which I really need solution to :

1. How can I have PHP execute properly under my username, not root.

2. How can I have PHP execute properly under the new web directory other than /var/www


Thank you so much in advance if anyone could shed some light upon me :KS:KS:KS:KS

---

### Post by mastablasta on 2020-09-25
how did you install PHP and Apache?

i never had this problem. root is normally only needed if any system files are accessed.

---

