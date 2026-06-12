---
title: "PHP: Need a second pair of eyes"
date: 2014-11-21
forum: Programming Talk
---

### Post by TheodoreP on 2014-11-21
so.....I need a second pair of eyes to take a close look at the code for my changecred.inc.php file and my savecred.inc.php. I can't seem to figure out why the passwords aren't submitting to the database? You can find the files over at [github]("https://github.com/NationalCoder/SociableCooking")!

---

### Post by TheodoreP on 2014-11-26
I'm still absolutely stumped with this issue here. I'm about to just create a new table for profile information. However I want to wait and get this issue fixed!

---

### Post by ofnuts on 2014-11-27
Have you checked the content of the $query variable before you submit it to the DB?

---

### Post by TheodoreP on 2014-11-29
alright......after taking a break from the project I have been able to realize that the issue is that when you click the update button it should go to index.php?card=savecred&id=Blah but instead it is going to index.php?searchFor=&card=search&firstName=Blah&email=blah@blah.blah&password=Blah&confirm=Blah&card=savecred&id=Blah!

I have no idea where to even start with this?

---

### Post by ofnuts on 2014-11-29
Can't help thinking about:

[QUOTE=Brian W. Kernighan]Everyone knows that debugging is twice as hard as  writing a program in the first place. So if you're as clever as you can  be when you write it, how will you ever debug it?[/QUOTE]

Yes, the [Brian Kernighan](http://en.wikipedia.org/wiki/Brian_Kernighan).

---

### Post by TheodoreP on 2014-11-30
I feel your trying to make fun of me, but I'll be honest.....I don't get the joke! I understand it is joke but that is about it. I lost with this issue because I have no idea where the script is calling the searchFor variable in the search.inc.php! Search still works, but I guess I crossed a wire somewhere  because the bomb is detonating when one tries to change their user credentials! I'm about ready to just create a new table/database, still haven't decided which one, to hold just the profile information (i.e. first and last names, age, gender, occupation, etc....) and just link the database/table to the userid in the users table. Is it even possible to link a column from one table to another table in a completely different database or do are foreign keys subject to the database they are created in?

---

### Post by pqwoerituytrueiwoq on 2014-11-30
when you submit data to the server check the post/get data that is being sent, you may have something in there wrong and you are going over ever line in the back end when your issues is in some javascript that formats the request or the html attributes

---

### Post by TheodoreP on 2014-11-30
I haven't actually put any javascript into the site yet! It's strictly php and mysql right now!

---

### Post by pqwoerituytrueiwoq on 2014-11-30
you have html right? check your form name attributes there and make sure they match what you are looking for in the php
if you don't see it have it dump a html comment on the replay page with the values and the names and make sure it is right

if i git clone that will it create the database and tables it needs to operate automatically? i really dont want to deal with setting up a database to debug that

---

### Post by ofnuts on 2014-11-30
> **MasterProgram said:**
> I feel your trying to make fun of me, but I'll be honest.....

No fun implied, just sharing the wisdom of the Great Old Ones.  If you don't even know where to start to debug, you didn't really understand what you wrote...

---

### Post by TheodoreP on 2014-12-01
Yeah, I'm just going to create a new database for the profile information. And I'll link the userid to the tables in the new database if it's possible!

---

### Post by TheodoreP on 2014-12-01
Alright, I know where the problem is!

After some soul searching and long hours of contemplating it appears that when I recoded the navigation area that I broke the site. 

here is the old messy version
[PHP]<?phpecho "<table width=\"20%\" border=\"0\" cellspacing=\"5\" cellpadding=\"0\" align=\"left\">\n";
echo "<tr><td><appname><a href=\"index.php\">SociableCooking</a></appname></td>\n";
echo "<td><form action=\"index.php\" method=\"get\">\n";echo "<input name=\"searchFor\" type=\"text\" id=\"searchF\">\n";echo "<input name=\"card\" type=\"hidden\" value=\"search\">\n";echo "</form></td></tr>\n";echo "</table>\n";
echo "<ul id=\"nav\">\n";    $userid = $_SESSION['recipeuser'];    $cardset = $_REQUEST['card'];    if($cardset != 'showrecipe')    {        $bookSET = $_REQUEST['card'];        echo "<li><strong>Catalog</strong><span class=\"darrow\">&#9660;</span>\n";        if($bookSET != 'community')        {            echo "<ul class=\"drop\"><li><a href=\"index.php?card=community\"><strong>Community Recipes</strong></a></li></ul>\n";        }else if($bookSET != 'dashboard')        {            echo "<ul class=\"drop\"><li><a href=\"index.php?card=myrecipes\"><strong>My Recipes</strong></a></li></ul>\n";        }        echo "</li>\n";        /* Show Post if your viewing the catalogs, yours or the communities, if           your viewing a single recipe make it vanish and if your viewing a recipe           other than your own display a spice-up link.        */        echo "<li><a href=\"index.php?card=newrecipe\"><strong>POST</strong></a></li>\n";    } else if($cardset = 'showrecipe') {        $recipeid = $_REQUEST['id'];        $query = "SELECT poster,spicer FROM recipes WHERE recipeid = $recipeid";        $result = mysql_query($query);        $row = mysql_fetch_array($result, MYSQL_ASSOC);        $poster = $row['poster'];        $spicer = $row['spicer'];        if($poster != $userid && $spicer == '') {            echo "<li><a href=\"index.php?card=spiceUP&id=$recipeid\"><strong>SPICE</strong></a></li>\n";        }     }
    $recipeid = $_REQUEST['id'];    // show comment, print and edit nav buttons only when card is set to a value of 'showrecipe'    if($cardset == 'showrecipe')    {        echo "<li><a href=\"index.php?card=newcomment&id=$recipeid\"><strong>Comment</strong></a></li>\n";        echo "<li><a href=\"print.php?id=$recipeid\" target=\"_blank\"><strong>Print</strong></a></li>\n";                $query = "SELECT poster FROM recipes WHERE recipeid = $recipeid";        $result = mysql_query($query) or die('Sorry we could not find the requested recipe.');        $row = mysql_fetch_array($result, MYSQL_ASSOC) or die('no records retrieved');                $poster = $row['poster'];                if(isset($_SESSION['recipeuser']) && $poster == $_SESSION['recipeuser'])        {            echo "<li><a href=\"index.php?card=updaterecipe&id=$recipeid\"><strong>Edit</strong></a></li>\n";        } else if($spicer == $userid) {            echo "<li><a href=\"index.php?card=updateSpice&id=$recipeid\"><strong>Edit</strong></a></li>\n";        } else {            echo "\n";        }
    }else    {        echo "\n";    }        echo "<li><strong>$userid</strong><span class=\"darrow\">&#9660;</span>\n";    echo "<ul class=\"drop\"><li><a href=\"index.php?card=myaccount&userid=$userid\">\n";    echo "<strong>Settings</strong></a></li>\n";    echo "<li><a href=\"index.php?card=logout\">(Logout)</a></li></ul>";
echo "</li></ul>\n";?>[/PHP]

and here is the new clean drop and toss menu version
[PHP]<?php/* This is the navigation include file for SociableCooking.com */echo "<table width=\"20%\" border=\"0\" cellspacing=\"5\" cellpadding=\"0\" align=\"left\">\n";    echo "<tr><td><appname><a href=\"index.php\">SociableCooking</a></appname></td>\n";    echo "<td><form action=\"index.php\" method=\"get\">\n";    echo "<input name=\"searchFor\" type=\"text\" id=\"searchF\">\n";    echo "<input name=\"card\" type=\"hidden\" value=\"search\">\n";    echo "</form</td></tr>\n";echo "</table>\n";/* This is the start of the unordered list drop and toss menus area.  * We begin with the catalog drop menu.*/$userid = $_SESSION['recipeuser'];$cardset = $_REQUEST['card'];echo "<ul id=\"nav\">\n";    if($cardset != 'showrecipe') {        $bookSET = $_REQUEST['card'];        echo "<li><strong>Catalog</strong><span class=\"darrow\">&#9660;</span>\n";        if($bookSET != 'community') {            echo "<ul class=\"drop\">\n";                echo "<li><a href=\"index.php?card=community\"><strong>Community Recipes</strong></a></li>\n";            echo "</ul>\n";        } else if($bookSET != 'dashboard') {            echo "<ul class=\"drop\">\n";                echo "<li><a href=\"index.php?card=myrecipes\"><strong>My Recipes</strong></a></li>\n";            echo "</ul>\n";        }        echo "</li>\n";    }/* This is the end of the catalog drop menu. * Now to begin work on the post menu. This especially trickery since I want a drop and toss menu for this.*/echo "<li><strong>Post</strong><span class=\"darrow\">&#9660;</span>\n";    echo "<ul class=\"drop\">\n";        echo "<li><strong>Recipe</strong>\n";            echo "<ul class=\"toss\">\n";                echo "<li><a href=\"index.php?card=newrecipe\"><strong>New</strong></a></li>\n";                if($cardset == 'showrecipe') {                    $recipeid = $_REQUEST['id'];                    $query = "SELECT poster, spicer FROM recipes WHERE recipeid = $recipeid";                    $result = mysql_query($query);                    $row = mysql_fetch_array($result, MYSQL_ASSOC);
                    $poster = $row['poster'];                    $spicer = $row['spicer'];
                    if($poster != $userid && $spicer == '') {                        echo "<li><a href=\"index.php?card=spiceUP&id=$recipeid\"><strong>Spice</strong></a></li>\n";                    } else                    if(isset($_SESSION['recipeuser']) && $poster == $userid) {                        echo "<li><a href=\"index.php?card=updaterecipe&id=$recipeid\"><strong>Edit</strong></a></li>\n";                    } else if($spicer == $userid) {                        echo "<li><a href=\"index.php?updateSpice&id=$recipeid\"><strong>Edit</strong></a></li>\n";                    }                    echo "<li><a href=\"index.php?card=newcomment&id=$recipeid\"><strong>Comment</strong></a></li>\n";                    echo "<li><a href=\"print.php?id=$recipeid\" target=\"_blank\"><strong>Print</strong></a></li>\n";                }            echo "</ul>\n";        echo "</li>\n";    echo "</ul>\n";echo "</li>\n";/* On to the next drop menu. * This time we focus on the user settings menu. * This will consist of the logout button and the settings buttons of course.*/echo "<li><strong>$userid</strong><span class=\"darrow\">&#9660;</span>\n";    echo "<ul class=\"drop\">\n";        echo "<li><a href=\"index.php?card=myaccount&userid=$userid\"><strong>Settings</strong></a></li>\n";        echo "<li><a href=\"index.php?card=logout\"><strong>Logout</strong></a></li>\n";    echo "</ul>\n";echo "</li>\n";echo "</ul>\n";?>
[/PHP]

please let me know if you find any discrepancies in the two files that could be causeing this bomb to go off! Either way now I know where to look!

---

### Post by TheodoreP on 2014-12-01
I got it figured out, turns out when I recoded the navigation file I forgot to close out the form for the search box! Now I feel really stupid, but I take it as a learning experience and a humbling one at that!

---

### Post by mörgæs on 2014-12-01
Good, please mark the thread 'solved'.

---

