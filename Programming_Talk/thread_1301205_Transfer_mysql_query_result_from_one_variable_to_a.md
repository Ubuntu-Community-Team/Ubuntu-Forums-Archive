---
title: "Transfer mysql_query result from one variable to another"
date: 2009-10-25
forum: Programming Talk
---

### Post by sdlynx on 2009-10-25
Hello,

I have:
> 
$result = mysql_query("SELECT * FROM stories ORDER BY RAND() LIMIT 1", $con);


And I need to get another variable $result2 which is the same as $result.  I have tried just $result2 = $result but it did not work, mysql_num_rows($result2) found the right number of rows but when I tried to while($row = mysql_fetch_array($result2)) it didn't loop even once.  Does anyone know how to properly get $result2 to equal $result?

SDLynx

P.S. This is PHP and MySQL.

---

### Post by januzi on 2009-10-25
Try:
> 
[COLOR=#000000][COLOR=Black]mysql_data_seek[/COLOR][COLOR=Black]([/COLOR][COLOR=Black]$result[/COLOR][COLOR=Black]2, 0[/COLOR][COLOR=#007700][COLOR=Black]);[/COLOR]
[/COLOR][/COLOR][COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]

---

### Post by sdlynx on 2009-10-25
> **januzi said:**
> Try:
[COLOR=#000000][COLOR=#007700]
[/COLOR][/COLOR]

in place for what?

---

### Post by januzi on 2009-10-25
Put it before while( $row = ...

---

### Post by sdlynx on 2009-10-25
> **januzi said:**
> Put it before while( $row = ...

wow, it worked! thanks!

---

