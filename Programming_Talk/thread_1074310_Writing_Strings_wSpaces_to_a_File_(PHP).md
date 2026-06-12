---
title: "Writing Strings w/Spaces to a File (PHP)?"
date: 2009-02-19
forum: Programming Talk
---

### Post by FireFoxer on 2009-02-19
Hi, I have a question.  When I prompt and get a string that will contain spaces, such as an address, and then print it to a file in PHP, the string is truncated at the first space.  Is there any way around this?  The code I am using is below.

[PHP]
<?php
$address = "";
$fout=fopen("file.txt", 'w')
printf("Enter the address: ");
fscanf(STDIN, "%s", $address);
fprintf($fout, "%s", $address);
fclose($fout);
?>
[/PHP]

---

### Post by geirha on 2009-02-19
fgets will read until '\n'. [http://php.net/fgets](http://php.net/fgets)

---

### Post by FireFoxer on 2009-02-19
Thanks very much, your tip solved my problem!:D

---

