---
title: "Glob PHP Subdirectory"
date: 2009-03-26
forum: Programming Talk
---

### Post by monk_rock on 2009-03-26
can anyone help me? This is my code. I am new and not very good at all.

<?
while ($row = mysql_fetch_array($result))

{
echo "<br />";
echo $row['mlsid'];
echo "<br />";
echo $row['address'];
echo "<br />";


foreach (glob($row['mlsid']."*101*") as $filename)
{
echo "<img height=100 width=100 src=".$filename.">";

}

}
mysql_close($db_link);


?>

It works great if I keep all the pictures in the same directory, but I want to put them in a subdirectory. It messes everything up.

How do I glob into a subdirectory.

Thank you, 
:confused:

---

### Post by Tibuda on 2009-03-26
Try glob("**/".$row['mlsid']."*101*")

---

