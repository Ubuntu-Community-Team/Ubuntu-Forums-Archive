---
title: "php mysql syntax"
date: 2007-06-10
forum: Programming Talk
---

### Post by adza on 2007-06-10
Hi guys,

      I'm having a real moment here, i believe my syntax in using mysql through php is out - bad.... for example, i have created a table where a user logs on with password, if successful, then a counter increments for the number of times visited the site... this i can query in mysql through the terminal and is working... no probs.. So, i have another bit that wants to check if this variable is 1 (indicating first time user logs on) so it can then redirect to a change password form... i would expect to do this... (assuming already connected to DB - column count is an integer)
```
 
$sql="select count from user where name='user'";
$query_count=mysql_query($sql);
if ($query_count == 1)
   { some code to redirect};
else
   {some other code};

```
this just doesn't seem to be working at all.... i would expect the value of $query_count would be equal to the integer stored in column 'count' after submitting this code.... is this correct? I think i'm missing something (probably fundamental) here.....

---

### Post by keithweddell on 2007-06-10
$query_count is a resource.  You need to add an extra line to access the value.  Something like:

```

$result = mysql_result($query_count,0);
echo $result;

```

or 

```

$result = mysql_fetch_assoc($query_count);
echo $result["count"];

```


Keith

---

### Post by adza on 2007-06-10
sweet... thanks! so then if my query returns an array, i could also use $result=mysql_result($query_count, 3); for the 3rd record for example?

---

### Post by Toxe on 2007-06-10
Generally do something like this:

```
$sql = "SELECT a, b, c, d FROM table WHERE ...";

$res = mysql_query($sql);

if (!$res)
  return NULL;  // error

// fetch the result row(s)
while ($row = mysql_fetch_assoc($res)) {
  // ... do some stuff ...
  echo $row["a"];
  $i = $row["b"] + $row["c"];
  // ... and so on ...
}
```

Of course if you only get one result row you can leave out the while loop.

---

