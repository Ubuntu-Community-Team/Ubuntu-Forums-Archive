---
title: "Mysql collation problem"
date: 2006-06-27
forum: Programming Talk
---

### Post by Isoss on 2006-06-27
I have mysql 5 client and server installed on my ubuntu system.

I have just inserted the first chapter of genesis into the database using SQL in phpmyadmin. Data are shown correctly with phpmyadmin, but when I retrieve the data with PHP data appear like ????? in the webpage.
Althought I have set the charset to windows-1256 using this PHP script:
```

<?php
mysql_connect("localhost","root","") or die ("error");
mysql_select_db("ecacsyr") or die ("error");
header('Content-Type: text/html; charset=windows-1256'); 
header('Content-Language: ar');
?>
<html dir="rtl">
<head>
</head>
<body>
<?php
$sql = "select * from `arabicbible`";
$result = mysql_query($sql);
echo "&#1575;&#1604;&#1603;&#1578;&#1575;&#1576; &#1575;&#1604;&#1605;&#1602;&#1583;&#1587;<br><br>&#1587;&#1601;&#1585; &#1575;&#1604;&#1578;&#1603;&#1608;&#1610;&#1606;<br><br>&#1575;&#1604;&#1575;&#1589;&#1581;&#1575;&#1581; &#1575;&#1604;&#1571;&#1608;&#1604;<br><br>";
while ($record = mysql_fetch_assoc($result))
{
	echo "<b>".$record['nid']." ".$record['verse']."</b><br>";
}
?>
</body>
</html>

```
And this is how it displays my data:
[img]http://nourelalam.org/Isos/bible.png[/img]

As you can see, data appear as ???? while other characters written in HTML they appear in arabic as they should.

So I have set the collation to cp1256_general_ci for the database, the table and the verse field which contains the arabic text.

Have a look at my phpmyadmin:
[img]http://nourelalam.org/Isos/genesis.phpmyadmin.png[/img]

Please help! 

I've never faced any problem with the collations before untill I upgraded to mysql5! before I never had to set any collation or work with anything related to charset in mysql ... phpmyadmin of my web host server doesn't have this problem at all! ... but I don't know why phpmyadmin gives this option on my localhost ... This is bugging me! and the strange thing is that when I removed mysql 5 completely from my system and reinstalled apache2 with the previous version of mysql and php4 and phpmyadmin and the problem remained! I don't really understand the mechanism of these web applications .. I just know php programming! So please somebody help!

---

### Post by Stromham on 2006-06-27
this is because your browser dosnt support the language, it has no clue what the charcters are so it puts ? in there place.

---

### Post by Isoss on 2006-06-28
Ok, how then it could read the first three lines:
&#1575;&#1604;&#1603;&#1578;&#1575;&#1576; &#1575;&#1604;&#1605;&#1602;&#1583;&#1587;

&#1587;&#1601;&#1585; &#1575;&#1604;&#1578;&#1603;&#1608;&#1610;&#1606;

&#1575;&#1604;&#1575;&#1589;&#1581;&#1575;&#1581; &#1575;&#1604;&#1571;&#1608;&#1604;

as you can see the browser can read arabic charachters which are set with the header as charset=windows-1256 ... As you can see, arabic data are shown in the tables of phpmyadmin, they are on the same PC, same browser ... but not shown in the webpage where data are retrieved with PHP!!!

The problem seems to be with the web applications!!! ... 

isn't there any solution? configuring mysql or something like that?

---

### Post by Stromham on 2006-06-28
then if you can read it, the server dosnt have the language support. so what you can do is have each word you use in english and use a switch statement.

---

### Post by Isoss on 2006-06-29
Excuse me ... I didn't get what you mean! I have a bible here. That's 66 books!!! ... I don't wanna create a solution! I need the solution that mysql has.

---

### Post by liza on 2007-06-17
Hi 
iam having the same problem also
iam trying to browse my data exists in phpmyadmin (arabic characters)
in phpmyadmin i can see it well
but in my browser i just get ??????
i tried to use many encoding but nothing??
did you find the solution for that, my server is unix too....

---

### Post by josef.sabl on 2008-01-22
I have this same problem. I think it is bug or wrong configuration of phpMyAdmin, not MySQL. I guess that phpMyAdmin probably uses wrong encoding when displaying contents of tables and inserting data into them.

Try it the other way around (this is how I usually work around this). Create PHP script, where you insert data using SQL queries. Data will be messed in phpMyAdmin, but they will look ok on the web page.

---

