---
title: "Limit PHP Description Field for Datafeed"
date: 2010-04-01
forum: Programming Talk
---

### Post by CrusaderAD on 2010-04-01
I have this script...

```
<? 
include("config.php");

unlink("feed.txt");

// Query DB Here
$result = mysql_query("select * from test") or die (mysql_error()); 
while ($row = mysql_fetch_array($result))
{

// Put something for the description if there isn't any
if($row[description] == ""){
$row[description] = "$row[name]";
}

// Strip out Trade Marks symbols from product name and descriptions
$row[name] = ereg_replace("™", "",$row[name]);
$row[name] = ereg_replace("&#153", "",$row[name]);
$row[name] = ereg_replace("&trade;", "",$row[name]);
$row[description] = ereg_replace("™", "",$row[description]);
$row[description] = ereg_replace("&#153", "",$row[description]);
$row[description] = ereg_replace("&trade;", "",$row[description]);

$line = "http://www.test.net/click-test-11111?url=http://www.test.com/test.asp?pid=$row[skew]&rid=PID|$row[name]|$row[description]|$row[package_type]|$row[retail]|$row[our_price]|$row[warnings]|$row[recuse]|$row[notes]|$row[ingredients]|$row[image]|$row[CatName]|$row[brand]|$row[category]|$row[skew]\n";

//Update Feed File Here
$fp = fopen("feed.txt", 'a'); // open new file for output
chmod("feed.txt", 0777);
fwrite($fp, $line); // write new format
fclose($fp); // close file

}
mysql_free_result($result);

header("Location: feed.txt");

?>
```

How do I limit the "Description" to 3000 characters?

---

### Post by Bachstelze on 2010-04-01
Generally, you limit the length of information when it is entered into the database, not when you retrieve it. How is your data entered?

---

### Post by CrusaderAD on 2010-04-01
Well lets say it's entered as text and I retrieve it. I want to limit it to 3000 characters when I do so and insert it into a datafeed txt file.

---

### Post by new_tolinux on 2010-04-01
You can limit it before you put it in a database by
[php]$var=substr($var,0,3000)[/php]I don't know for sure if it's possible to use the "maxlength" attribute in a HTML <TEXTAREA>.

---

### Post by s_ø on 2010-04-01
Hi.
Instead of ereg_replace you should use str_replace.
Edit: ereg_replace is for use with regular expressions and you just need a basic replace function. ereg_replace is also deprecated as of PHP 5.3.0 and if you need regular expressions you should use preg_replace instead.

[PHP]$search = array("™","&#153", "&trade;");
$replace = "";
$row[name] = str_replace($search, $replace, $row[name]);
$row[description] = str_replace($search, $replace, $row[description]);[/PHP]To trim description to 3000 use substr as new_tolinux writes.
[PHP]$row[description] = substr($row[description], 0, 3000);[/PHP]You cannot trust the "maxlength" in html forms, and you should always validate your data before inserting in database.

---

### Post by new_tolinux on 2010-04-01
> **s_ø said:**
> You cannot trust the "maxlength" in html forms, and you should always validate your data before inserting in database.
You should not trust it indeed.
Take UTF-8 for example: you can specify 3000 Chinese chars (all multibyte). That will almost certainly produce an error when you try to put it into a MySQL field with a maximum of 3000 characters.

Assuming the input is coming from a "POST", you can use (as said)
[php]
$var=substr($var,0,3000);
[/php]

If not you should always use:
[php]
$var=substr(mysql_real_escape_string($var),0,3000);
[/php]
OR
[php]
$var=substr(htmlentities($var),0,3000);
[/php]

---

