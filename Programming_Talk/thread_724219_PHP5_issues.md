---
title: "PHP5 issues"
date: 2008-03-14
forum: Programming Talk
---

### Post by Squizz on 2008-03-14
I'm trying to follow a tutorial on webmonkey to build a basic php/mysql website but I can't seem to get the GET command to work properly.

I'm attempting [this]("http://www.webmonkey.com/webmonkey/99/21/index3a_page3.html?tw=programming") tutorial, and while I understand the principles of it and how it should work, it doesn't seem to be working on my site.  I've amended my code to reflect my settings (below) and it seems right.

However, the php will list the rows from the table, but when I try to view a single record nothing happens.  [HERE]("http://www.simontucker.net/cms/get4.php") is a live version of my code.  It starts at get4.php (which lists all records) and if you click a link, the url will change to get4.php?id=7 or something but the page will remain the same.

I have put up a [phpinfo page]("http://www.simontucker.net/cms/details.php") in case it's something in my configurations, but I really don't understand why it isn't working!

Here's the code I am using for the page too:

[PHP]
<html>

<body>

<?php



$db = mysql_connect("localhost", "root")

mysql_select_db("cms",$db);

// display individual record

if ($id) {

   $result = mysql_query("SELECT * FROM content WHERE id=$id",$db);

   $myrow = mysql_fetch_array($result);

   printf("Username: %s\n<br>", $myrow["user"]);

   printf("Category: %s\n<br>", $myrow["cat"]);

   printf("Title: %s\n<br>", $myrow["title"]);

   printf("Content: %s\n<br>", $myrow["content"]);

} else {

    // show employee list

   $result = mysql_query("SELECT * FROM content",$db);

    if ($myrow = mysql_fetch_array($result)) {

      // display list if there are records to display

      do {

        printf("<a href=\"%s?id=%s\">%s %s</a><br>\n", $PHP_SELF, $myrow["id"], $myrow["user"], $myrow["title"]);

      } while ($myrow = mysql_fetch_array($result));

    } else {

      // no records to display

      echo "Sorry, no records were found!";	

    }

}



?>



</body>



</html>
[/PHP]

---

### Post by mssever on 2008-03-14
How is the $id variable being set? You aren't setting it to anything before testing it. Perhaps you mean $_GET['id']. I didn't read the tutorial (or your other links), but I'm wondering if it was written with the assumption that register_globals is on (which was the default in PHP 4 and earlier). Register_globals is a major security hole, so you should always disable it in php.ini or your .htaccess file. If the tutorial is in fact using register_globals, then it's outdated and you should find a better tutorial--or just read the PHP manual.

Also, read up on SQL injection. The PHP manual has a section on this. Dumping a variable directly into a query is an invitation for someone to do all kinds of Bad Things to your site, data, and users.

---

### Post by Squizz on 2008-03-14
Thank you very much.

I added 
[php]
$id=$_GET['id']; 
[/php]

And it did what it was supposed to do :)

---

