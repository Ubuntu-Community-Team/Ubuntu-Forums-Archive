---
title: "SQL, WHERE, and LIKE"
date: 2009-10-25
forum: Programming Talk
---

### Post by sdlynx on 2009-10-25
Hi all,

I'm working on a script that will search through a database and retrieve all entries where the word sdlynx is written anywhere in the story field or comments field, and here is my code:
```
SELECT * FROM stories WHERE (story LIKE '%sdlynx%' OR comments LIKE '%sdlynx%') ORDER BY dateTime DESC LIMIT 0,15
```

The code runs perfect in PHPMyAdmin's SQL query box (returning around 15 rows), but when I use mysql_query() it returns 0 rows.  Help?

SDLynx

---

### Post by -grubby on 2009-10-25
Well, just to be clear here, you're using PHP, right?

---

### Post by sdlynx on 2009-10-25
> **-grubby said:**
> Well, just to be clear here, you're using PHP, right?

Yes, PHP.

---

### Post by Elfy on 2009-10-25
moved to programming

---

### Post by Exershio on 2009-10-25
show us the full code for the query bit

edit: be sure you're calling mysql_fetch_assoc(); you can also use mysql_fetch_row(), but I prefer assoc so you can reference the results by field name instead of $result[0] and $result[1], etc

example:

$query = mysql_query("blah blah");
$result = mysql_fetch_assoc($query);

echo $result['field_name'];

---

### Post by januzi on 2009-10-25
You can always put
> 
echo $query.' '.mysql_error() ;

after the line with the mysql_query.

---

### Post by sdlynx on 2009-10-25
actually I have been using:
> 
$query = "SELECT * FROM stories WHERE (story LIKE '%sdlynx%' OR comments LIKE '%sdlynx%') ORDER BY dateTime DESC LIMIT 0,15";
$result = mysql_query($query, $con /* connection */) or die(mysql_error());
while($row = mysql_fetch_array($result) {
     echo $row[story];
}


---

### Post by OpenGuard on 2009-10-25
[php]$query = mysql_query("SELECT * FROM stories WHERE (story LIKE '%sdlynx%' OR comments LIKE '%sdlynx%') ORDER BY dateTime DESC LIMIT 0,15") or die(mysql_error());
$entries = mysql_num_rows($query);

echo "Query returned $entries entries.";[/php]What's the output ?

---

### Post by Tony Flury on 2009-10-25
Could it be something simple like some database engines don't understand the LIMIT clause ?

---

### Post by sdlynx on 2009-10-25
> **Tony Flury said:**
> Could it be something simple like some database engines don't understand the LIMIT clause ?

Doubtful, considering I am using it elsewhere on the site just fine.

> **OpenGuard said:**
> [php]$query = mysql_query("SELECT * FROM stories WHERE (story LIKE '%sdlynx%' OR comments LIKE '%sdlynx%') ORDER BY dateTime DESC LIMIT 0,15") or die(mysql_error());
$entries = mysql_num_rows($query);

echo "Query returned $entries entries.";[/php]What's the output ?

returns 15 entries...., but when I try to fetch them it returns 0 entries....

EDIT: Oh gosh, I feel like an idiot. Turns out I was editing the wrong part of the code.  Thanks for the help though guys, it works now.

---

### Post by OpenGuard on 2009-10-25
[php] 
$query = mysql_query("SELECT * FROM stories WHERE (story LIKE '%sdlynx%' OR comments LIKE '%sdlynx%') ORDER BY dateTime DESC LIMIT 0,15") or die(mysql_error());
 
while ($data = mysql_fetch_array($query)) {
    echo $data['story'] . "<hr>";
}
[/php]

---

