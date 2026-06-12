---
title: "Need help displaying MySQL data in PHP"
date: 2007-10-30
forum: Programming Talk
---

### Post by thenetduck on 2007-10-30
Hi
I would like to display one piece of data from my MySQL database without using the whole 
```



while($row = mysql_fetch_assoc($field))
{
   extract($row);
   return $what_i_really_want;
}
```

Does anyone know how to do this easy? For instance, I have an ID of a row and want the name in table person. Do I really need a while loop for each extraction? 

Thanks

The Net Duck

---

### Post by dataw0lf on 2007-10-30
Just call mysql_fetch_assoc once:
```
$row = mysql_fetch_assoc($field);
echo $row['name'];
```

---

### Post by smartbei on 2007-10-30
So long as your table is set up so that the field you are checking is unique, you are safe doing what dataw0lf suggested above. To be safe though you may want to check the number of rows returned:
[php]
$num_rows = mysql_num_rows($result);
if ($num_rows == 1) {
     $row = mysql_fetch_assoc($field);
     echo $row['name'];
}else {
     echo "Error! too many rows returned";
}
[/php]

---

