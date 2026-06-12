---
title: "troubleshooting my pear installation"
date: 2007-07-28
forum: Programming Talk
---

### Post by digby on 2007-07-28
I'm having some trouble getting pear working on my server (Ubuntu 7.04, Apache 2.2.3, MySQL 5.0, php 5.2.1). I'm certain my LAMP setup is working fine as I can use php to connect to my db and run queries. I have thus far, however, failed to get the db connection to work via pear.

I installed pear from the repository and used it to install the database module.  
[LEFT]```
$pear list
Installed packages, channel pear.php.net:
=========================================
Package          Version State
Archive_Tar      1.3.2   stable
Console_Getopt   1.2.3   stable
DB               1.7.12  stable
PEAR             1.6.1   stable
Structures_Graph 1.0.2   stable
```[/LEFT]
 The code I used to test the connection is below. I added several print statements to try to find where it was failing, and the output is nothing but the first line ("Attempting to connect to MySQL database...")

Any help would be appreciated.
[php]
<?php 

// Required imports 
require_once('/usr/share/php/DB.php'); 

echo ("Attempting to connect to MySQL database...<br />"); 

// Initiate the MySQL connection     
$connection = DB::connect("mysql://testuser:testpass@localhost/test"); 
echo ("Connected...<br />"); 

// Test the connection 
if (DB::isError($connection)){die ("Couldn't connect!<br />".DB::errorMessage($connection));} 
echo ("DB::isError done...<br />"); 

?> [/php]

---

### Post by bbzbryce on 2007-07-29
> **digby said:**
> 
[php]
<?php 

// Required imports 
require_once('/usr/share/php/DB.php'); 

echo ("Attempting to connect to MySQL database...<br />"); 

// Initiate the MySQL connection     
$connection = DB::connect("mysql://testuser:testpass@localhost/test"); 
echo ("Connected...<br />"); 

// Test the connection 
if (DB::isError($connection)){die ("Couldn't connect!<br />".DB::errorMessage($connection));} 
echo ("DB::isError done...<br />"); 

?> [/php]

First you should turn on error reporting and should only have to include 'DB.php':

[PHP]<?php
error_reporting(E_ALL);
require_once 'DB.php';
?>
[/PHP]

Doing the first should only be done in debug mode but should give you some more useful output. If pear is setup properly then DB.php will be on the php path. Post any further errors you get after getting error_reporting to display.

---

### Post by digby on 2007-07-29
Well, the bad news is that error_reporting(E_ALL); didn't add any additional output, but after I changed my require_once statement and modified my path line in php.ini back to /usr/share/php (I had changed it before to /usr/share/php/PEAR/) everything seems to be working now... I just have no idea why that fixed it.

Thoughts?

Oh, and thanks for the help!

---

### Post by bbzbryce on 2007-07-29
> **digby said:**
> Well, the bad news is that error_reporting(E_ALL); didn't add any additional output, but after I changed my require_once statement and modified my path line in php.ini back to /usr/share/php (I had changed it before to /usr/share/php/PEAR/) everything seems to be working now... I just have no idea why that fixed it.

Thoughts?

Oh, and thanks for the help!

Yeah.. DB.php is in /usr/share/php not /usr/share/php/PEAR. If you want to see debugging output you'll have to enable it in your php.ini file via the display_errors flag.

---

### Post by digby on 2007-07-29
So why didn't it work when I explicitly stated the path to DB.php?

---

### Post by bbzbryce on 2007-07-29
> **digby said:**
> So why didn't it work when I explicitly stated the path to DB.php?

Ah yes, you did to that:

From DB.php
```
require_once 'PEAR.php';
```

That would not be found if the path wasn't setup correctly.

---

### Post by digby on 2007-07-29
ah!  It all begins to make sense....

thanks!

---

