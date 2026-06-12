---
title: "PHP include script problem"
date: 2009-04-21
forum: Programming Talk
---

### Post by Adina on 2009-04-21
I am trying to make an include function on a website but it does not work. The php code shows up as cleartext when I open the html page in a browser. I can't figure out what I'm doing wrong here. Can someone please help?

This is the php code that is on the html page :

<$php include ('includes/menu.inc.php');

$>


And this is the menu.inc.php file :

<ul id="nav">
        <li><a href="index.php" id="here">Home</a></li>
        <li><a href="journal.php">Journal</a></li>
        <li><a href="gallery.php">Gallery</a></li>
        <li><a href="contact.php">Contact</a></li>
    </ul>

---

### Post by odyniec on 2009-04-21
It's "<?php", not "<$php".

---

### Post by Adina on 2009-04-21
Thank's for your quick reply, I really appreciate it. I changed the code and it works fine now. Thank's again!! :D

---

