---
title: "php session variable pains, is this right?"
date: 2011-01-22
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-22
I have 2 forms 
first one was called mysearch2.htm
I had to rename to mysearch2first.php !!

and put this code in it to eliminate the session vars??
I had to unset first, otherwise they were not destroyed.

> <?php
session_start();
unset($_SESSION['wo1']);
unset($_SESSION['wo2']);
unset($_SESSION['wo3']);

unset($_SESSION['ws1']);
unset($_SESSION['ws2']);
unset($_SESSION['ws3']);
unset($_SESSION['ws4']);

session_unset();
session_destroy();
$_SESSION = array();
?> 

I use these session vars in mysearch2.php
in mysearch2first.php, a user inputs some search words
mysearch2first then goes to mysearch2.php and $_POST is used to pull the various words to search.

then mysearch2.php calls itself over and over and needs to reuse those search words in queries, etc.... 

what happens if I want a third page called mysearch3.php, how can I even consider using session vars since I cant destroy them and use them at the same time?
What to do?

---

