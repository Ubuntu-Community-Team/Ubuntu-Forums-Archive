---
title: "php / mysql help"
date: 2007-07-26
forum: Programming Talk
---

### Post by dhtseany on 2007-07-26
hey all this may be an easy one but i'm new to php and mysql. 

while attempting to use an example piece of code, i encountered this error:

[**_screen shot 1_**]("http://img337.imageshack.us/my.php?image=temp1dr9.jpg")

This is my code for test.php:

[**_screen shot 2_**]("http://img238.imageshack.us/my.php?image=temp2jh5.jpg")

My connection should be fine. If I remove the small block of code causing the errors, no errors appear.

Any ideas?


Thanks,

Sean

---

### Post by Note360 on 2007-07-26
er in the mysql_fetch_array($results) the results variable inst defined yet so it has nothing in it so yeah. instead of $results I ithnk you ment to put in $request or you can set $results equal to $request

---

