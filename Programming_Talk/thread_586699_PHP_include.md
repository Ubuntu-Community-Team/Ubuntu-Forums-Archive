---
title: "PHP include"
date: 2007-10-22
forum: Programming Talk
---

### Post by DouglasAWh on 2007-10-22
Sorry for the crappy thread title, I hit enter too soon!

I have an HTML page that I've built with XQuery.  Unfortunately, the original document has lots of escaped HTML charaters "<" = "&lt" and thus the browser renders the characters, not the HTML (it shows the '<', not keeping that just in source).  My thought at correcting this was to use the html_entity_decode function in PHP, but the problem is even though it's simple to include my XQuery output in the PHP file with the include command, I don't know how to turn that include into a strong some that html_entity_decode can do its thing.  I'm going to continue to look at it, but any help would be greatly appreciated as always!

---

### Post by DouglasAWh on 2007-10-22
Ok, now I'm trying to do this with regular expressions, but I don't have any experience with regular expressions.  Here's what I've got

```

$a = include 'google2.html';


$b = preg_replace("/&lt;/", "/</", $a);
preg_replace("/&gt;/", "/>/", $b);

```

It throws no errors, but doesn't do what I think it should do, either.

Interestingly, $a = include 'google2.html'; outputs the document, so I'm wondering if it is actually passing the variable to $a.  If I put the echo $a command it, it produces a '1' after the code for some reason.

---

### Post by LaRoza on 2007-10-22
It looks like you want to open a file, read the contents, and then process it.

Use:

fopen,fread,file_get_contents, and other file handling functions.

[http://www.php.net/manual/en/function.file-get-contents.php](http://www.php.net/manual/en/function.file-get-contents.php)

---

### Post by #Reistlehr- on 2007-10-22
you can do something along the lins of..

<?php
$File = 'Path To File';
$Contents = file_get_contents($File);
echo html_entity_decode($Contents);
?>

(not garunteed to work)

---

### Post by DouglasAWh on 2007-10-22
I actually already had this figured out, but hadn't posted the solution.

Here it is (basically what #Reistlehr- said):

```

<?php

$a = file_get_contents('google2.html');
$b = html_entity_decode($a);
echo $b;

?> 

```

Nice and simple. :)

---

