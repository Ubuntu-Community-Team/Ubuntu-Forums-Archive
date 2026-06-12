---
title: "PHP - Class 'GladeXML' not found !"
date: 2012-04-18
forum: Programming Talk
---

### Post by etdsbastar on 2012-04-18
Hello friends,

A simple code :

[PHP]<?php
$glade = new GladeXML('test.glade');

Gtk::main();
?>[/PHP]

is giving me the error :
PHP Fatal error:  Class 'GladeXML' not found in ... on line 2

Please help me friends...

---

### Post by fallenshadow on 2012-04-18
Probably a really silly question but.. did you create a .glade file for it to use?

Glade files need to be created by Glade itself.

---

### Post by etdsbastar on 2012-04-25
Dear,

Glade file has already been created as test.glade.

The php error showing that class GLADEXML not found...

Any help...

---

### Post by etdsbastar on 2012-04-27
Please help friends !!!

---

### Post by etdsbastar on 2012-05-01
Any help please... bump...

---

### Post by etdsbastar on 2012-05-01
I anyhow managed to recompile phpgtk and resolved the problem of GladeXML but now it is showing another problem.

when i am running the file,
It is displaying nothing.

Please help.

$php <filename.php>

is showing nothing.

---

