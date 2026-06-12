---
title: "Help understanding some PHP/MySQL - should be easy for your guys :)"
date: 2007-10-29
forum: Programming Talk
---

### Post by thenetduck on 2007-10-29
HI
I am learning PHP / MySQL with a Wrox book (good stuff) and need some help understand a part of it. 

In the book you create a fake movie review website. I am at the point where we created a database and I am now calling values from it to appear on the website. I don't understand how the while and the foreach works. 

```

<?php	
// connect to MySQL
$connect = mysql_connect("localhost", "username","password") or die ("yo nigga roche you didn't connect!");

// make sure I am selecting the right db
mysql_select_db("moviesite");

$query = "SELECT movie_name, movie_type " . 
			"FROM movie " . 
			"WHERE movie_year>1990 " .
			"ORDER BY movie_type";
			
$results = mysql_query($query) or die(mysql_error());

while ($row = mysql_fetch_assoc($results))
	{
		foreach($row as $val1)
		{
			echo $val1;
			echo " ";
		}
		echo "<br />";
	}
?>

```

as you can see there is some $val1 variable and it doesn't explain how assoc works etc. I can program in c++ so am not unfamiliar with whiles and for loops but this one has me scratching my head. 

One more question while I'm here. When values are stored in results how are they stored? in an array? If so where does that array start with the table? Wrox is good, but doesn't go into any detail to enlighten me on this subject. 

Thank you everyone! 

The Net Duck

---

### Post by smartbei on 2007-10-29
Here are some answers :):

$result is not an array, it is a mysql result object, with the resulting rows themselves accessed through mysql_fetch_assoc,mysql_fetch_aray, and several others of the same vein.

mysql_fetch_assoc fetches an associative array (that is, one in which the keys are strings), with the keys being the names of the columns in the mysql database table. Something that is very helpful when inspecting arrays is:
```

echo "<pre>";
print_r($array);
echo "</pre>";

```
Which recursively prints out the array and its keys in an ordered fashion.

So say you have a table with the columns 'id', 'name' and 'title'. $row would hold, for each iteration of the while, a resulting row's values. $row['id'] is the id, $row['name'] is the name and $row['title'] is the title. Simple and very readable. In your case it would hold of course only $row['movie_name'] and  $row['movie_type'].

The while just checks if $row is set, (the mysql_fetch_array sets it). If there are no more rows in the resulting set from the database, it returns someling like Null or 0 and the while exits.

The foreach just loops through all of the keys in $row and sets their value to $val1. There is an alternative form of foreach:
```

foreach($row as $key => $val1) {
     echo "$key => $val1";
}

```
Which lets you access the key as well (note- didn't check syntax, might be a bit off).

Lastly, if I remember correctly it is also possible to access a associative array's values through normal keys ($arr[1], $arr[0], etc.) so print_r($arr) might show them as keys as well.

Hope that clears things a bit!

---

### Post by thenetduck on 2007-10-30
Hey Thanks for the help, it reallly DID help me. Ok so I get how eveything works now but  I still have a little bit of a problem understanding mysql_fetch_assoc() I know that it gets the table object (so to speak) but how does it differ from mysql_fetch_array() ? 

Again, This really helped so thanks!

The Net Duck

---

### Post by smartbei on 2007-10-30
Have you tried print_r($row); ? Try it once with array and once with assoc.

The difference is that assoc returns the values with the keys to them being the names of their columns. array returns the values with the keys to them being the order of them in your sql statement (I am pretty sure anyway), starting from 0.

---

### Post by thenetduck on 2007-10-30
OH ok that makes sense. I did try printing the assoc but not the array. On my way to print the array (oh geeze....) hee. Thanks Smartbei


The Net Duck

---

### Post by carlosjuero on 2007-10-31
mysql_fetch_assoc($result_string), as smartbei says, fetches the results and returns them via named keys ('name', 'id', etc), mysql_fetch_array($result_string) fetches them into a numbered array (also as smartbei says :)); there is a third option, mysql_fetch_row($result_string) which fetches it as both. All 3 have their uses, but for ease of understanding what the code is doing it is usually best to use _array.

---

