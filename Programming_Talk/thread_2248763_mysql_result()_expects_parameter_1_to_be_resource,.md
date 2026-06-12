---
title: "mysql_result() expects parameter 1 to be resource, boolean given in"
date: 2014-10-16
forum: Programming Talk
---

### Post by Jaesya on 2014-10-16
here my coding...

<?php
$conn=mysql_connect("localhost","username","password") 
or die(mysql_error());
$db=mysql_select_db("dbname",$conn);
 
   
$query = "SELECT data,filetype FROM uploads where id=$id"; 
$result = MYSQL_QUERY($query); 
$data = MYSQL_RESULT($result,0,"data"); 
$type = MYSQL_RESULT($result,0,"filetype"); 
 Header( "Content-type: $type"); 
 print $data; ?>
 
<div class="rect">
<a href="download.php?filename=<?php echo $filename ;?>" >
</div>


the error detected at line $data and $type it says that:

[COLOR=#404040][FONT=Lucida Grande]mysql_result() expects parameter 1 to be resource, boolean given in[/FONT][/COLOR]


this coding about downloading files from database.. i don't know where the mistake... can anyone help me to solve this... i'm still new to this language... thanks! :)

---

### Post by spjackson on 2014-10-17
mysql_query returns FALSE if the query fails. You should test for this and display the error.
```

$result = MYSQL_QUERY($query); 
if (!$result) {
    die('Invalid query: ' . mysql_error());
}

```
You should also check that mysql_select_db is successful.

In the code you posted, $id is not set - maybe that's your problem. (It could be set elsewhere of course.)

---

### Post by SeijiSensei on 2014-10-17
While debugging, I usually have PHP echo the query string so I can make sure it's correct.  So I'd add
```
echo $query;
```
after the query is specified.

---

