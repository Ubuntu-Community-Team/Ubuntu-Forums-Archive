---
title: "[SOLVED] MySQL query not returning all matching data"
date: 2008-08-04
forum: Programming Talk
---

### Post by mike_g on 2008-08-04
I'm having a problem with MySQL somewhere. When I generate a filtered query its not always returning all the matching results. And I cant seem to find any pattern to this. The image below has a query echoed:
[IMG]http://i92.photobucket.com/albums/l15/mikegrundel/mysql_borked.png[/IMG]

This should return 2 items, but only one appears. I checked the db to make sure that the language and categories were correctly typed; so thats not the problem. Does anyone have any idea what may be causing this?

Cheers.

Edit: heres the code too if that helps
```
	$link = mysql_connect($localhost, $username, $password);
	mysql_select_db($database);
	
	$criteria = "";
	if($_GET['lang'] && $_GET['cat'])
	{
		if($_GET['lang'] != "All") $criteria = " WHERE language = '".$_GET['lang']."'";
		if($_GET['cat'] != "All")
			if($criteria != "")
				$criteria = $criteria." AND (category1 = '".$_GET['cat']."' OR category2 = '".$_GET['cat']."')";
			else
				$criteria = $criteria." WHERE (category1 = '".$_GET['cat']."' OR category2 = '".$_GET['cat']."')";
	}

		
	$query = "SELECT * FROM snippet".$criteria;
	echo $query;
	
	$result = mysql_query($query);
	$i = 0;
	$listing = array();
	while($row = mysql_fetch_object($result))
	{
		$list_left[$i] = "<tr><td><div class='link_box'><a href='snippet.php?id=$row->id'>";
		$list_name[$i] = $row->name;
		$list_right[$i]= "</a></div></td><td class='link_language'>".$row->language."</td>
						  <td class='list_description'>".$row->summary."<td></tr></form>";
		$i++;
	}
	mysql_close($link);
	mysql_free_result($result); 
```

Edit2: >_< I found the problem, my for loop to draw the page was not iterating to the last result. Why do I seem to always solve my problems immediately after posting, lol

---

### Post by drubin on 2008-08-04
I would take a look at mysql_real_escape_string it is a way to provent sql injection/hacking.

---

### Post by mike_g on 2008-08-04
Yeah, thats one thing I have left to do.

---

### Post by drubin on 2008-08-05
> **mike_g said:**
> Yeah, thats one thing I have left to do.

Try and do it while you are working, as a rule of habit, If you go back and try and do them after you might forget things = hacked.

---

