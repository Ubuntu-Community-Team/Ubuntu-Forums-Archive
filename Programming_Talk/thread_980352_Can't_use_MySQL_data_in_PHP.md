---
title: "Can't use MySQL data in PHP?"
date: 2008-11-12
forum: Programming Talk
---

### Post by Gannon8 on 2008-11-12
Hi. I have a LAMPPP Server 8.10, and I have a problem.
When I try to use the text gotten from MySQL in the following PHP script:
[PHP]<?php
  include 'connect_website.inc.php';
  $database = mysql_select_db("website_db") or die("ERROR: Cannot access database");
  
  $data = mysql_query("SELECT * FROM links");
  print "<!-- STARTING LINKS -->";
  while($row = mysql_fetch_array($data, MYSQL_ASSOC))
  { 
    if($row["approved"] != True)
    {
      continue;
    }
    print "<tr>\n";
    print "    <td><a href=\"gotourl.php?link={$row['name']}\">{$row['name']}</a></td>\n";
    print "    <td>$row['desc']</td>\n";
    print "    <td>$row['clicks']</td>\n";
    print "</tr>\n";
    print "\n";
  }
  print "<!-- END LINKS -->";
?>[/PHP] The page complains $row['desc'] is not of type 'str.' A var_dump, however, reveals that it is a string. The row from the table is in this format:
varchar url, varchar name, varchar desc, unsigned int clicks, tinyint approved
Please help?

---

### Post by Gannon8 on 2008-11-13
Bump

---

### Post by Gannon8 on 2008-11-13
Anyone? :confused:

---

### Post by cabalas on 2008-11-13
In PHP when referencing an element in an array like you have been the array must be surrounded with { and } like so:

[PHP]print "<td>{$row['clicks']}</td>\n";[/PHP]

or you can concatenate the strings like so: 

[PHP]print "<td>" . $row['clicks'] . "</td>\n";[/PHP]

It pretty much comes down to you using whatever you think looks better.

---

### Post by Gannon8 on 2008-11-13
Oh, hey it works. I thought it complained about a syntax error when I tried that...

---

