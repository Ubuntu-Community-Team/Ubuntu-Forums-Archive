---
title: "question about DB queries"
date: 2006-02-25
forum: Programming Talk
---

### Post by oldmanstan on 2006-02-25
i have a mysql table that i want to pull rows out of and stuff them into objects in php. i can either query the DB and have it return a series of arrays with the values for each column (ex: $name[0] and $email[0] would be the values for the first row... etc.) or i could do several queries.

basically the question is which is more expensive in terms of server usage: one large query or several smaller queries?

my gut instinct tells me the large query would be better but i was wondering if anyone has any input?

---

### Post by sas on 2006-02-25
Executing multiple queries would probably take longer. Definetly so if you aren't using persistant connections.

Try both with a crude benchmark.
<?php
$time_start = microtime(true);

//your script here

$time_end = microtime(true);
$time = $time_end - $time_start;

echo "Execution time: $time seconds\n";
?>

---

### Post by sapo on 2006-02-25
I ve always used the less number of queries possible, and you should really consider using the mysql LIMIT function, or you can slow everything on your site with this query :p

---

### Post by LordHunter317 on 2006-02-25
Always minimize queries, and do as much work on the DB side as possible.  It's faster than you.

---

### Post by oldmanstan on 2006-02-25
thanks guys, looks like my instinct was right, cool

---

