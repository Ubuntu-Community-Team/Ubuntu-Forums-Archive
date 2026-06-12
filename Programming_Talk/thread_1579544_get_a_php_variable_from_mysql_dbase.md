---
title: "get a php variable from mysql dbase?"
date: 2010-09-22
forum: Programming Talk
---

### Post by garyed on 2010-09-22
I'm trying to figure out how to retrieve a number from a mysql database at a specific column & row using php.
If I run mysql in a terminal & do:

    select new from goods where type="chair"; 

then I'll get > 
| new       |
|-----------|
| 50        |
------ -----

If I do in a php file:
```

 $result =mysql_query('select new from goods where type="chair"');  

```
it doesn't work.
I'm trying to get that number 50 so i can use it as a variable to add or subtract with.
I don't have any problems connecting to the database in the php file so at least I know that's not the problem.
Any help appreciated

---

### Post by Finalfantasykid on 2010-09-22
You are probably forgetting to fetch the row.

```

$rows = array();
while ($row = mysql_fetch_array($result)) {
    $rows[] = $row;
}

```

Then you can access the value by indexing the $rows array.  for something like this, I always do a count() just to make sure that the result set is not empty.

```

if(count($rows) > 0){
    $new = $row[0]['new'];
}

```

---

### Post by garyed on 2010-09-22
I'm still not getting it to work but thanks for the help anyways.

---

### Post by Finalfantasykid on 2010-09-22
Did you remember to select which database you are using?  This is usually done right after you connect to the database.

Also, this is probably not the problem, but I don't normally use those types of quotes for something like that.

$result =mysql_query("select new from goods where type='chair'");
For strings I like to use double quotes, and for shorter things like single characters, a single quote I use.  I doubt this is causing the problem, as php for the most part will allow both.

Are you getting any errors at all?

---

### Post by garyed on 2010-09-23
> **Finalfantasykid said:**
> Did you remember to select which database you are using?  This is usually done right after you connect to the database.

Also, this is probably not the problem, but I don't normally use those types of quotes for something like that.

$result =mysql_query("select new from goods where type='chair'");
For strings I like to use double quotes, and for shorter things like single characters, a single quote I use.  I doubt this is causing the problem, as php for the most part will allow both.

Are you getting any errors at all?

Thanks,

I think the quotes made the difference because I was using variables for "new" & "chair". I ended up using another example I got somewhere else & it didn't work either at first. I don't think the quotes made a difference when I wasn't using variables but with variables it would only work the way you showed it here. Double quotes had to be on the outside.
Thanks again

---

### Post by Finalfantasykid on 2010-09-23
Yes, if you have variables within single quotes ie: 'This is a $variable' it will take it literally, and not evaluate the value of $variable.  Double quotes however will.  That must have been the problem.

---

### Post by soltanis on 2010-09-23
[php]
$rc = mysql_query("select new from goods where type='chair';");
$result = mysql_fetch_array($rc);
[/php]

---

