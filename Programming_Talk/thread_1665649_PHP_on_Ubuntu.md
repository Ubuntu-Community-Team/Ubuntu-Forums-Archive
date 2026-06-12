---
title: "PHP on Ubuntu"
date: 2011-01-12
forum: Programming Talk
---

### Post by thunderstruck1 on 2011-01-12
Hi guys, I'm new at Ubuntu and I have the following problem - i  installed XAMPP and get Apache and MySQL running but when I'm trying to  run some basic PHP code it doesn't run. I tried with the most simple  command - echoing something. And when I save the page in .php format the  browser (Firefox) doesn't open it and when I try in .html with embedded  php in it it doesn't display anything. 

Thank you in advance!
[B]
_P.S. - I already posted the same topic in the beginner section, so if some moderator is reading this - you can delete the other topic, i think it's better to be here._[/B]

---

### Post by thunderstruck1 on 2011-01-14
... any ideas?

---

### Post by lisati on 2011-01-14
You might want to look into php-cli as an alternative to firing up a browser to run your PHP code.

---

### Post by roccivic on 2011-01-14
[removed silly reply, had misread the opening post]

---

### Post by sdowney717 on 2011-01-14
running in the browser not displaying perhaps due to errors in php code

i know this works, puts up 2 input boxes on the screen with text.
put this in an empty file and call it something.php
then run it by going to localhost/something.php

> <html>
<head>
<basefont face="Arial">
</head>
<body>

<?php

if (!isset($_POST['submit'])) {
// form not submitted
?>

    <form action="<?=$_SERVER['PHP_SELF']?>" method="post">
    Title: <input type="text" name="btitle">
    Author: <input type="text" name="bauthor">
    <input type="submit" name="submit">
    </form>

<?php
}
else {



  

} //last curly comes from top if submit else statement
?>

</body>
</html>

---

### Post by thunderstruck1 on 2011-01-14
The problem was that the .php files I tried to run were outside the htdocs folder. Embarrassing. :oops: Thank you for the help though. :)

---

