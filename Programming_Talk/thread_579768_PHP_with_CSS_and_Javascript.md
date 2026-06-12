---
title: "PHP with CSS and Javascript"
date: 2007-10-18
forum: Programming Talk
---

### Post by DouglasAWh on 2007-10-18
There's a couple things I want to do.

First off, I want to turn URLs into active links, either at the input layer or the export layer...doesn't really matter to me.

Secondly, I want to arrange a MySQL query to look like items like an online business (though this isn't for a business).  What I mean, is I'd like to pull an item name and a picture and have a list of the said items displayed appropriately.

Right now, my code looks like:

```

$fieldsHandle = mysql_list_fields ($dbname, $table);
$numFields = mysql_num_fields ($fieldsHandle);


   /* submit the query */   
   SetType ($query, "string");
   $query = "SELECT * from " . $table;
   
//set resultHandle
   $resultHandle = mysql_query( $query, $conn ) or die ("Could not get DB");

   /* table headers */
   echo "<table border='1'>\n";
   echo "<tr bgcolor='red'>\n";
   
   $i = 0;
   while ($i < $numFields) {
   //set fName
      $fName = mysql_field_name($fieldsHandle, $i);
      echo "<td><b>$fName</n></td>\n";
      $i++;
   }
   echo "</tr>\n";
   
   /* table rows */
   $numRows = mysql_num_rows ($resultHandle);
   $i = 0;
   while ($i < $numRows) {
      echo "<tr>\n";
      $j = 0;
      while ($j < $numFields) {
         $fName = mysql_field_name($fieldsHandle, $j);
         $fieldValue = mysql_result ($resultHandle, $i,  $fName);
	 echo "<td>$fieldValue</td>\n";
	 $j++;
      }
      echo "</tr>\n";
      $i++;
   }
   echo "</table>\n";


```

This works just fine, but doesn't give me the option to exclude fields.  I'd actually like to exclude several fields and the URL field I think I want to put in the item name field and make the item picture a link.  I could potentially move things around with CSS but my CSS (as well as Javascript and PHP) are somewhat weak (I'm learning!).  To me, it seems like there is probably a function that will take certain fields and display them in some ordered fashion.  I know I can return one field at a time with

```

$query  = "SELECT eid FROM emp";
$result = mysql_query($query);

while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    echo "EID :{$row['eid']} <br>";
} 

```

The problem with this approach, of course is that the rows will be one after another, which is where a CSS solution might come in.  I'm just wondering what people think the best solution to this is.

Thanks!

---

### Post by #Reistlehr- on 2007-10-18
you can select multiple fields using, 

$query  = "SELECT FIELD1, FIELD3, FIELD3, and so one FROM TABLE";

if you do, *, it will select every field

---

### Post by DouglasAWh on 2007-10-18
The problem is, when I do 

```

$query  = "SELECT id, name FROM wishlist";
$result = mysql_query($query);

echo "<div id=\"name\">";
while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    echo "EID :{$row['id']['name']}<br />";
}
echo "</div>";

```

as you suggest, only 'id' shows up in the HTML.  I'm assuming the problem is with the line while($row = mysql_fetch_array($result, MYSQL_ASSOC)).

---

### Post by #Reistlehr- on 2007-10-18
> **DouglasAWh said:**
> The problem is, when I do 

```

$query  = "SELECT id, name FROM wishlist";
$result = mysql_query($query);

echo "<div id=\"name\">";
while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
    echo "EID :{$row['id']['name']}<br />";
}
echo "</div>";

```

as you suggest, only 'id' shows up in the HTML.  I'm assuming the problem is with the line while($row = mysql_fetch_array($result, MYSQL_ASSOC)).



Try:

$query  = "SELECT id, name FROM wishlist";
$result = mysql_query($query);

echo "<div id=\"name\">";
while($row = mysql_fetch_**assoc**($result, MYSQL_ASSOC))
{
    echo "EID :{$row['id']}{$row['name']}<br />";
}
echo "</div>";

i think you had a misunderstanding about the mysql_fetch_array/assoc array outputs.

---

### Post by KCPokes on 2007-10-18
Have you tried to split up your reference?  

```

    echo "EID :{$row['id'].$row['name']}<br />";

```

Your query looks accurate and loading the results into row looks good, thus I'd start with your reference statement.

---

### Post by DouglasAWh on 2007-10-18
I kept the mysql_fetch_array function but change the last line to     

```
echo "EID :{$row['id']}{$row['name']}<br />";
```

Working great!  I have to prettify it a bit, but so far so good.  THANKS!

---

### Post by #Reistlehr- on 2007-10-18
NP

mysql_fetch_assoc will associate each array key as the field name, where as mysql_fetch_array will create a numerical and an associative keyname. It saves resources to use mysql_fetch_assoc.

Just an FYI!

have fun!

---

### Post by DouglasAWh on 2007-10-18
Why does 


   ```
echo "<a href=\"{$row['link']}\"><img src=\"img/{$row['pic']}\" /></a><a href=\"{$row['link']}\">{$row['name']}</a>{$row['description']}<br />";

```
work, but 

```
if ({$row['bought']} == 0)
   { echo "<a href=\"{$row['link']}\"><img src=\"img/{$row['pic']}\" /></a><a href=\"{$row['link']}\">{$row['name']}</a>{$row['description']}<br />";
}
``` 

not work?

In fact, with the curly brackets PHP barfs.  Without the {} in the if statement, it does not exclude those values with 1.  Bought is a boolean.

EDIT: If the examples on [http://www.php.net/while](http://www.php.net/while) are correct, then an if can be nested in a while, which is one thing I was curious about.  I'll post another edit when I have additional info.

---

### Post by #Reistlehr- on 2007-10-18
> **DouglasAWh said:**
> Why does 


   ```
echo "<a href=\"{$row['link']}\"><img src=\"img/{$row['pic']}\" /></a><a href=\"{$row['link']}\">{$row['name']}</a>{$row['description']}<br />";

```
work, but 

```
if ({$row['bought']} == 0)
   { echo "<a href=\"{$row['link']}\"><img src=\"img/{$row['pic']}\" /></a><a href=\"{$row['link']}\">{$row['name']}</a>{$row['description']}<br />";
}
``` 

not work?

In fact, with the curly brackets PHP barfs.  Without the {} in the if statement, it does not exclude those values with 1.  Bought is a boolean.

EDIT: If the examples on [http://www.php.net/while](http://www.php.net/while) are correct, then an if can be nested in a while, which is one thing I was curious about.  I'll post another edit when I have additional info.


Your problem is simple.  ({$row['bought']} == 0)

The only time you use {}'s are when you are wanting to return a variable that is placed between double quotes. Ex echo "Hello {$User}";

For this instance, inside the while() statement, do 

if($row['bought'] == 0)

---

### Post by DouglasAWh on 2007-10-18
it'd be nice if it was that simple, but the if statement simply does not work.  If bought == 1, then it still returns the value.  It's true it doesn't give an error, but I mentioned that in the post previous to Reistlehr's.

EDIT: ok, it turns out that using != returns nothing and using === also returns nothing.  Why are 1 and 0 behaving the same?  I've also tried true and false since it is a boolean.  


```

+----+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+--------------------------+-------+--------+--------------+---------------------------------------------------+
| id | name                                           | link                                                                                                                            | pic                      | price | bought | type         | description                                       |
+----+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+--------------------------+-------+--------+--------------+---------------------------------------------------+
|  1 | Ubuntu for Non-Geeks                           | http://www.amazon.com/Ubuntu-Non-Geeks-2nd-Project-Based-Get-Things-Done/dp/1593271522/ref=pd_ybh_1/                            | ubuntu-for-non-geeks.jpg |    24 |      0 | NULL         | NULL                                              |
|  0 |                                                |                                                                                                                                 |                          |     0 |      0 |              |                                                   |
|  5 | Tributo a Rage Against the Machine: En Espanol | http://www.amazon.com/gp/product/B000BITTG2/ref=wl_itt_dp/105-0037493-7858860?ie=UTF8&coliid=I1JTIXHE9VG45Y&colid=19JF9BHR2207N | rageTribute.jpg          |    16 |   NULL | Rage Tribute | A tribute to Rage Against the Machine in Spanish. |
| 10 | Weights                                        | yo                                                                                                                              | test                     |    25 |      1 | weights      | hey                                               |
+----+------------------------------------------------+---------------------------------------------------------------------------------------------------------------------------------+--------------------------+-------+--------+--------------+---------------------------------------------------+


```

As you can see, bought where name='weight' is 1.

---

### Post by #Reistlehr- on 2007-10-18
can you post your whole while statement?

---

### Post by DouglasAWh on 2007-10-18
> **#Reistlehr- said:**
> can you post your whole while statement?

```

while($row = mysql_fetch_array($result, MYSQL_ASSOC))
{
	if($row['bought'] == 0)
   { echo "<a href=\"{$row['link']}\"><img src=\"img/{$row['pic']}\" /></a><a href=\"{$row['link']}\">{$row['name']}</a><br />{$row['description']}<br /><br />";
}
   }

```

also, note that I edited my last post to show the table from which the query is pulling.

---

### Post by DouglasAWh on 2007-10-18
Might as well post the URL too: [http://www.ils.unc.edu/~whitdoug/668/form/wishlist.php](http://www.ils.unc.edu/~whitdoug/668/form/wishlist.php)

---

### Post by #Reistlehr- on 2007-10-18
try

if($row['bought'] == '0')

---

### Post by DouglasAWh on 2007-10-19
that's a great idea, but doesn't work.  I changed the type from boolean to int to see if that made any difference...nope.

Perhaps it is just testing once?  I wouldn't have thought that since it is looping through for each other instance.  I'll test that theory tomorrow by just changing the value on the first return from the array.  Right now, I'm tired and going to bed.  I get to share the stage with Michael Tiemann for a while tomorrow and I am so very unprepared...ugh.

---

### Post by #Reistlehr- on 2007-10-19
Ok, the only thing i can think of is, you are not including the field in the mysql query.

I used what you had here, and made a mock table/script from the one on the previous page, and it worked fine. i had mine query all the fields though. 'SELECT * FROM TABLE'

---

### Post by DouglasAWh on 2007-10-20
> **#Reistlehr- said:**
> Ok, the only thing i can think of is, you are not including the field in the mysql query.

I used what you had here, and made a mock table/script from the one on the previous page, and it worked fine. i had mine query all the fields though. 'SELECT * FROM TABLE'

Ok, I feel like an idiot!  It wasn't in the query.  Works great now!!!!!!  I haven't had a chance to finish it yet, but I'll probably have some more questions later.  Hopefully all the questions will be things I actually am confused about and not stupid things like leaving something out of a query...

---

### Post by #Reistlehr- on 2007-10-20
No problem. That's why we are here.

---

### Post by pmasiar on 2007-10-21
> **#Reistlehr- said:**
>  i had mine query all the fields though. 'SELECT * FROM TABLE'

Just nitpick: as IT pro, you should never advise to use "SELECT * FROM" -- it is just bad SQL practice, and you probably can explain why if you think about it. :-)

---

### Post by #Reistlehr- on 2007-10-22
> **pmasiar said:**
> Just nitpick: as IT pro, you should never advise to use "SELECT * FROM" -- it is just bad SQL practice, and you probably can explain why if you think about it. :-)
Yeah, but it's irrelevant in this case. Any of the published code, i never use a wildcard. It's illogical, open to SQL injections, and wastes resources. For this i was testing his code to make sure it was actually working, minus the lack of fields to be queried on his end, which ended up being the problem

---

