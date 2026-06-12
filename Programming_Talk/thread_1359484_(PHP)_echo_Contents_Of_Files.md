---
title: "(PHP) echo Contents Of Files"
date: 2009-12-19
forum: Programming Talk
---

### Post by Chamillionaire2 on 2009-12-19
What's Up?

Basically, Is it possible via the magic of php, To echo the contents of multiple files in a folder if you don't know the name, Of course you would need to use a wild card of some sort.

Example
[php]
$var = echo "folder/*.html";
echo $var
[/php]

Any Ideas?

Thanks Bye.

---

### Post by Bachstelze on 2009-12-19
Well you could always use the backtick operator or the shell_exec() fonction with "cat folder/*.html". If you want to do it purely in PHP, you'll have to loop through the directory contents using readdir() and other file-related functions.

---

### Post by Physical Hook on 2009-12-19
opendir and readdir should be what you are looking for.

P.S. - Regardless of whether your magical echo statement works or not, you'll need an array.

---

### Post by Hellkeepa on 2009-12-20
HELLo!

The recommended way of doing this, is with "[glob()](http://no.php.net/glob)" and "[readfile()](http://no.php.net/readfile)", if you want to output directly, or "[file_get_contents()](http://no.php.net/file_get_contents)", if you want to do something about the file's contents before printing it out.
Like this:
```
<?php
foreach ($glob ('folder/*.html') as $File) {
    readfile ($File);
}
?>
```
Happy codin'!

---

