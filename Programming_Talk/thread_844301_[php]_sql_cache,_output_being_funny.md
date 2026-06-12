---
title: "[php] sql cache, output being funny"
date: 2008-06-29
forum: Programming Talk
---

### Post by ELD on 2008-06-29
When looping through categorys and forums all the categorys are displayed, but only 1 forum from the first category gets displayed, and gets displayed in each category :S

This first file is the one that sorts out the actual cache
[php]
class sql_cache
{
	// this check to see if we need to update the cache at this time
	// this is only ever called if a cache has specifically been marked to update
	function start($name)
	{
		// find the update field for the cache asked
		$sql_check = "SELECT `cache_update` FROM `cache` WHERE `cache_name` = '{$name}'";
		$query_check = mysql_query($sql_check) or die(mysql_error());
		$check = mysql_fetch_array($query_check);
		
		// if we need to update the cache
		if ($check['update'] == 1)
		{
			$function = "cache_$name";
			$function();
		}
	}
	
	// update the category cache
	function cache_categorys()
	{
		$file = "cache_categorys.cache";

		$query = "SELECT * FROM `forums` WHERE `is_cat` = 1 ORDER BY `order` ASC";
		$result = mysql_query($query) or die (mysql_error());
		while ($record = mysql_fetch_array($result)) 
		{
			$records[] = $record;
		}
		$output = serialize($records);
		$fp = fopen($file,"w");
		fputs($fp, $output);
		fclose($fp);
	}
	
	// update forums cache
	function cache_forums($parent)
	{
		$file = "cache_forums.cache";

		$query = "SELECT * FROM `forums` WHERE `parent` = {$parent} ORDER BY `order` ASC";
		$result = mysql_query($query) or die (mysql_error());
		while ($record = mysql_fetch_array($result)) 
		{
			$records[] = $record;
		}
		$output = serialize($records);
		$fp = fopen($file,"w");
		fputs($fp, $output);
		fclose($fp);
	}
}
[/php]

This files is the one that outputs the categorys and forums
[php]
include('class_sql_cache.php');

class forums
{
	function categorys_output()
	{
		$file = 'cache_categorys.cache';
		if (file_exists($file))
		{
			$records = unserialize(file_get_contents($file));
		}
		else
		{
			$sql_cache = new sql_cache();
			$sql_cache->cache_categorys();
			$records = unserialize(file_get_contents($file));
		}
		
		// Query results are in $records array
		foreach ($records as $id=>$row) 
		{
				echo "<strong>{$row['name']}</strong><br />";
				$this->forums_output($row['fid']);
		} 
	}
	
	function forums_output($parent)
	{
		$file = 'cache_forums.cache';
		if (file_exists($file))
		{
			$records = unserialize(file_get_contents($file));
		}
		else
		{
			$sql_cache = new sql_cache();
			$sql_cache->cache_forums($parent);
			$records = unserialize(file_get_contents($file));
		}
		
		// Query results are in $records array
		foreach ($records as $id=>$row) 
		{
				echo "{$row['name']}<br />";
		} 
	}
	
	function sub_forums_output()
	{
	}
}
[/php]

And this is my test page:
[php]
mysql_connect("localhost","username", "password"); 

mysql_select_db('database');

include('class_forums.php');

$forums = new forums();

$forums->categorys_output();
[/php]

But it shows this:
```

Prxa.info
News, Updates & Information
General Chat Here
News, Updates & Information
PXBulletin
News, Updates & Information

```

:(

---

### Post by Jordanwb on 2008-06-29
What is it supposed to output? To be honest I don't understand what's going on here.

---

