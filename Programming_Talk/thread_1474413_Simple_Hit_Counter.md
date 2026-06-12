---
title: "Simple Hit Counter"
date: 2010-05-06
forum: Programming Talk
---

### Post by hawaiian1der on 2010-05-06
How in the world do you make a simple hit counter in PHP? I cannot get it to work no matter what I do. Please help.

---

### Post by Penguin Guy on 2010-05-06
Have you tried [googling it]("http://www.google.com/search?q=PHP+Hit+Counter")?
[LIST]
[*][http://www.totallyphp.co.uk/scripts/text_file_hit_counter.htm](http://www.totallyphp.co.uk/scripts/text_file_hit_counter.htm)
[*][http://www.developingwebs.net/phpclass/hitcounter.php](http://www.developingwebs.net/phpclass/hitcounter.php)
[/LIST]

---

### Post by hawaiian1der on 2010-05-06
Neither worked.

---

### Post by Penguin Guy on 2010-05-06
If you gave us a [FONT="Courier New"].tgz[/FONT] of your code and some more information about the problems you're experiencing then maybe we could help you better. Also, make sure you have PHP installed on the webserver you're trying to run it on.

---

### Post by hawaiian1der on 2010-05-06
This is what I have for the script. It stays on 1.

---

### Post by Penguin Guy on 2010-05-14
[PHP]
$count_my_page = ("hitcounter.txt");
$fp = fopen($count_my_page , "w");    # Open the file before reading it
$hits = (int)file($fp);               # Convert string to integer
$hits ++;                             # Remove '[0]' - integer is not an array
fputs($fp, "$hits");                  # (again) Remove '[0]'
fclose($fp);
echo $hits;                           # (again) Remove '[0]'
[/PHP]
Sorry for the slow response, I've been trying to install Apache to test this on, but haven't had any luck - so no promises that it'll work.

[COLOR="Red"]**EDIT:** Does not work.[/COLOR]

---

### Post by Penguin Guy on 2010-05-15
My test server is finally up and running thanks to the IRC folk at #httpd. I believe you are facing two problems:
[LIST=1]
[*]The file permissions are wrong and the webserver cannot write to the file. Simply run:
```
chgrp www-data hitcounter.txt
chmod 662 hitcounter.txt
```
[*]The script is written incorrectly. Here is the tested, working, version:
[PHP]
<?php 

$FILE = "hitcounter.txt";

// Open the file for reading 
$fp = fopen($FILE, "r") or die("<p>Error: Cannot read from file.</p>"); 

// Get the existing count 
$count = fread($fp, 1024); 

// Close the file 
fclose($fp); 

// Add 1 to the existing count 
$count = $count + 1; 

// Display the number of hits 
echo "<p>Page views: " . $count . "</p>"; 

// Reopen the file and erase the contents 
$fp = fopen($FILE, "w") or die("<p>Error: Cannot write to file.</p>"); 

// Write the new count to the file 
fwrite($fp, $count); 

// Close the file 
fclose($fp); 

?> 
[/PHP]
[/LIST]

---

### Post by hawaiian1der on 2010-05-19
Thank you, that is partly what I needed.

---

### Post by soltanis on 2010-05-19
South Carolina eh. Sounds like my neck of the woods.

Anyway, you should also be using file locking:

[php]
if (!flock($fp, LOCK_EX)) {
    die("could not lock the file");
}

# do stuff
# release lock

flock($fp, LOCK_UN);
[/php]

That way two instances of this script running won't clobber each others counts but one will wait for the other.

---

### Post by Penguin Guy on 2010-06-20
> **hawaiian1der said:**
> Thank you, that is partly what I needed.
If you need more information please tell us what you want to know. Otherwise, it would help others if you could mark this as solved through [COLOR="Green"]Thread Tools -> Mark this Thread as Solved[/COLOR]. Thanks :)

---

