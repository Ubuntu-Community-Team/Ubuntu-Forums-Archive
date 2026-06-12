---
title: "problem with echo command in php??"
date: 2009-08-10
forum: Programming Talk
---

### Post by kuldeepsidhu on 2009-08-10
[PHP]
	echo '<h2><p align=center>Poetry</p></h2>';
	mysql_select_db("website",$con);
	$result=mysql_query("SELECT heading,text FROM poetry");
	
	while($row = mysql_fetch_array($result))
  {
  echo   $row['heading']."<br/>".$row['text'];
  echo "<br/><br/><hr width=80%/><br/>";
  }
[/PHP]

by deafult the heading and the text are display in left..
but i want to display them in center...how can i do that..?i have used <p align=center> it dose not work...plz tell me with giving example from this code.....and can we change the colors of the display text..how to do that.tell me by using internal css in this file..

---

### Post by ddarsow on 2009-08-10
> **kuldeepsidhu said:**
> [PHP]
	echo '<h2><p align=center>Poetry</p></h2>';
	mysql_select_db("website",$con);
	$result=mysql_query("SELECT heading,text FROM poetry");
	
	while($row = mysql_fetch_array($result))
  {
  echo   $row['heading']."<br/>".$row['text'];
  echo "<br/><br/><hr width=80%/><br/>";
  }
[/PHP]

by deafult the heading and the text are display in left..
but i want to display them in center...how can i do that..?i have used <p align=center> it dose not work...plz tell me with giving example from this code.....and can we change the colors of the display text..how to do that.tell me by using internal css in this file..

For starters, why do you have a <p> tag wrapped in a <h2>? more to the point though it should be ```
<P align=\"center\">
``` as it needs to be in quotes and those must be escaped in the php echo.

AS for the font color, the easiest way to do that is with a span such as: [HTML]<span style=\"color:#ffff00;\">text</span>[/HTML]

---

### Post by Tibuda on 2009-08-10
Use CSS. PHP is for data handling, HTML for content structuring, and CSS for styling.

---

### Post by hessiess on 2009-08-10
Go and read through [http://htmldog.com/](http://htmldog.com/). Then learn how to use a PHP framework like [http://cakephp.org/](http://cakephp.org/).

---

