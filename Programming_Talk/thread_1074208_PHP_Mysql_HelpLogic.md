---
title: "PHP Mysql Help/Logic"
date: 2009-02-19
forum: Programming Talk
---

### Post by cerealtx on 2009-02-19
Okay, i have working code, that gets information from a webpage, but then im going to do stuff with that information, but i don't want to duplicate it, how can i check my mySQL database for a entry am i going to have to go through the entire table each time? because after each user thats not on it, im going to do the "stuff" to the information then add that info to the database so its not repeated, could i just search for that information in the database? like
```

$result = mysql_query("SELECT Name FROM table WHERE Name='info'");
while($row = mysql_fetch_array($result))
  {
if(!result)
{
echo "not found..."
do whatever...
  }

```

but see like that, its going to have to go through the entire database, while it wont take long it still seems like a waste

---

### Post by konqueror7 on 2009-02-19
i use ```
if (mysql_affected_rows($connection) != 0) { // code if someting is found} else { // code when something is not found }
```

i don't quite understand what you meant, but this how i do it so i save time not entering the loop...

---

### Post by junaid123 on 2009-02-19
you can give the table name. i think if you give the table name instead of the database it will only traverse the specific table each time.  but honesty i did not understand your question or problem

---

### Post by simeon87 on 2009-02-19
If I understand correctly, you're trying to check the existence of a row in a table in a database? As a small optimization, you could add ' LIMIT 1' to the end of the query so it'll stop searching as soon as it has found a row; because now, it'll search the whole table for all rows with Name='info'.

---

### Post by cerealtx on 2009-02-19
does this seem logical? sorry about my horrible attempt at explaining myself
```

$result = mysql_query("SELECT Name FROM table WHERE Name="$info" LIMIT 1");
while($row = mysql_fetch_array($result))
  {
if($row['Name] == $info)
{
already in database, skip
}
else
{
do compulations, then
insert into database
}
}
```

---

