---
title: "MySQL + php problem."
date: 2007-06-19
forum: Programming Talk
---

### Post by jingo811 on 2007-06-19
I learnt to do some webpages in WAMP at a nightcourse.  I managed after 2 months to finally install LAMP correctly and it seems from testing phpinfo.php MySQL is working fine.
My test site is supposed to list a bunch of items it works in WAMP but I get this error in LAMP.

> Warning: mysqli_num_rows() expects parameter 1 to be mysqli_result, boolean given in /var/www/test/x/lista2.php on line 16
Warning: mysqli_free_result() expects parameter 1 to be mysqli_result, boolean given in /var/www/test/x/lista2.php on line 69

Can you see what causes this problem which never happened in WAMP?

> 
<?php



$sql = "SELECT article_id, title, PRIS, description

	FROM clothes

	ORDER BY title";



$resultat = mysqli_query($dbLink, $sql);

$antal_rader = mysqli_num_rows($resultat);    [COLOR="Red"]Line 16!!!!!![/COLOR]

print "<p><b>Det finns " . $antal_rader . " artiklar i webshoppen.</b></p>";
...
...

---

### Post by winch on 2007-06-19
You should check the result of [mysqli_query]("http://php.net/mysqli_query") to make sure the query succeeded.

I suspect the query fails for some reason and you are passing FALSE into [mysqli_num_rows]("http://php.net/mysqli_num_rows").

---

### Post by perlude on 2007-06-19
Well, I can't find any error in your PHP script, except the value of $dbLink, I believe it's a connection variables, so check $dblink first for an error, wheter there is a connection between your script and database or not.

Check with PHP Manuals at php.net, there are tons of information there.

HTH.

---

### Post by jingo811 on 2007-06-19
tnx for visiting me.  I solved it it seems that my tables named i.e. Clothes was forced being named clothes in WAMP but when I try to port it to LAMP I neeeded to change the query in my PHP script so that it finds Clothes.
Bad explanation, but things are OK now.

---

