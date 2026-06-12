---
title: "Help needed in creating catalog - PHP/MySQL"
date: 2007-12-14
forum: Programming Talk
---

### Post by Jawahir on 2007-12-14
I'm working on my graduation project at the moment, which is basically an online supermarket. I'm having difficulty with the catalog for the supermarket's products (I'm new to this programming business).

For the catalog, I have two pages, one html and the other is the action page in php. For the html page I have this code:


> <form action="catalog.php" method="POST">
Category : <select name="category">
<option value="fresh food">Fresh Food</option>
<option value="kitchen cupboard">Kitchen Cupboard</option>
<option value="frozen food">Frozen Food</option>
<option value="drinks">Drinks</option>
<option value="toiletry and baby">Toiletry and Baby</option>
<option value="house">House</option>
</select><br />
<input type="submit" value="Submit Info" />
</form> 

This works fine. The problem is with the PHP action page. I'm not quite sure how to do that part. So far I've done this:

> <?
include ("mysqlconnect.inc.php");

$category = $_POST['category'];

$query = "SELECT * FROM resource WHERE category ='$category'"; //checks the database for categories matching the credentials entered
$result=mysql_query($query);

if (mysql_num_rows($result) >= 1) { //checks to see if there are any positive matches



I don't know how to to retrieve the data from the resource table in my database (which lists all the products) according to the category selected in the html page. In other words, I haven't a clue what to write next in that code! If anyone can help then please let me know as soon as possible (the deadline is approaching!).

P.S. The resource table (which holds all the products) is this:

> CREATE TABLE `resource` (
  `resource_id` int(10) NOT NULL auto_increment,
  `name` varchar(50) collate ascii_bin NOT NULL default '',
  `category` enum('fresh food','kitchen cupboard','frozen food','drinks','toiletry and baby','house') collate ascii_bin NOT NULL default 'fresh food',
  `purchase_price` decimal(10,2) NOT NULL default '0.00',
  `description` text collate ascii_bin NOT NULL,
  PRIMARY KEY  (`resource_id`)
) ENGINE=InnoDB DEFAULT CHARSET=ascii COLLATE=ascii_bin AUTO_INCREMENT=3 ;

P.P.S. I know that most tend to have another table for the categories, but unfortunately I didn't do that and that is why none of the tutorials available online for shopping carts have helped me much.

---

### Post by pedro_orange on 2007-12-14
This is how I used to fetch stuff from SQL when I used to write php 4 years ago :)

Hope this helps

```
if($result)

			{

	

				while($blah = mysql_fetch_row($result))

				{

					$result[1] //First column of row [2] for 2nd etc
                                        //Do whatever
			

				}wend;




			}

else

			{

                                 //Nothing
	

			}
```

EDIT: Forgive the awful formatting, it's C&P

---

### Post by geirha on 2007-12-14
I would use [mysql_fetch_assoc](http://www.php.net/manual/en/function.mysql-fetch-assoc.php).  (Check out that link, there's an example of how to use it).

---

### Post by Jawahir on 2007-12-14
Thank you!

This is what I used (if anyone's interested!):

> 
if (mysql_num_rows($result) >= 1) { //checks to see if there are any positive matches
	while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    echo "Name : {$row['name']} <br>" .
		 "Purchase Price: {$row['purchase_price']} <br>" .
		 "Description: {$row['description']} <br><br>";
		}
}
	
else echo "There are no products listed.";

---

### Post by sunset_studies on 2007-12-14
> **Jawahir said:**
> 
$category = $_POST['category'];

$query = "SELECT * FROM resource WHERE category ='$category'"; //checks the database for categories matching the credentials entered
$result=mysql_query($query);



Just FYI (who knows, it might get you a better mark):

to prevent SQL injection, always escape user data. In your case:

$query = "SELECT * FROM resource WHERE category ='".mysql_real_escape_string($category)."'";

Also, you'd normally use the category ids as the <option> values,  not the category strings... and of course change the query accordingly.

Ok I will stop now.

---

### Post by rich.bradshaw on 2007-12-16
```
 $query = "SELECT * FROM resource WHERE category ='$category'";
```The problem with that is when someone enters something like this into the category box:

```
x'; DROP TABLE "resource"; 
```in other words, that will run the query:

```
 $query = "SELECT * FROM resource WHERE category ='x'; DROP TABLE "resource";";
```Which will delete the resource table. Not good!

Even though you have a dropdown box in you html, you can still type what you like using javascript.

Look up sql injection, as mentioned above you need to escape special characters.

---

