---
title: "php and select count"
date: 2011-01-13
forum: Programming Talk
---

### Post by sdowney717 on 2011-01-13
I have a query which works in the query analyzer

SELECT COUNT(id) as num FROM bookdata WHERE titles like 'd%'

but, i cant figure it out in PHP

from a pagination eam[ple, I have this, but it gives me nothing

```

 /// START of MySQL results &#8211; Page numbering
 /// Count total

 $query2 = "SELECT COUNT(id) as num FROM bookdata WHERE titles like 'd%'";

 $WHERE = "WHERE titles like 'd%'";
 $totals = mysql_result(mysql_query(&#8221;SELECT COUNT(id) as Num FROM bookdata $WHERE &#8220;),0); 

 $totals = mysql_result(mysql_query($query2,0));

```
 
etc...
no matter how i try and jigger it
I assume I am supposed to get a number back.

---

### Post by sdowney717 on 2011-01-13
>   $totals = mysql_result(mysql_query("SELECT COUNT(id) FROM bookdata where titles like '$btitle%'"),0);

this one works, finally!

---

