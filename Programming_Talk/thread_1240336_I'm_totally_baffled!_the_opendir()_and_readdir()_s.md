---
title: "I'm totally baffled! the opendir() and readdir() strange!"
date: 2009-08-14
forum: Programming Talk
---

### Post by kapi on 2009-08-14
I'm new to php and am having a little trouble understanding why when I run some code that the out put is not in the order I expect.

code:
--------
<?php
 
//Open images directory
$dir = opendir("ads");

//List files in images directory
while (($file = readdir($dir)) !== false)
  {
  echo "filename: " . $file . "<br />";
  }
closedir($dir);
 
?>

output:
---------

filename: two.txt
filename: .
filename: five.txt
filename: four.txt
filename: three.txt
filename: ..
filename: one.txt

----------

Any help would be very much appreciated

---

### Post by MadCow108 on 2009-08-14
[http://us.php.net/manual/en/function.readdir.php](http://us.php.net/manual/en/function.readdir.php)
> Returns the filename of the next file from the directory. The filenames are returned in the order in which they are stored by the filesystem.

---

### Post by kapi on 2009-08-14
so what would I use to ensure the output is performed in a set patter such as 1 to 5 or a - z.

---

### Post by MadCow108 on 2009-08-14
[http://us.php.net/manual/en/function.scandir.php](http://us.php.net/manual/en/function.scandir.php)

or put you files in an array and sort it how ever you like

---

