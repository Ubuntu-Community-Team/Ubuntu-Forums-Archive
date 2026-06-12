---
title: "store images in mysql using php"
date: 2008-08-13
forum: Programming Talk
---

### Post by Elisei on 2008-08-13
help :confused:

 i am trying to store a curled image in mysql. 
 
 the code is as follows:

[PHP]<?php

$ch = curl_init("some url .jpg");
curl_setopt($ch, CURLOPT_HEADER, 0);
curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($ch, CURLOPT_BINARYTRANSFER,1);
$im= curl_exec($ch);
curl_close($ch);

  $im_ = addslashes($im);

  $connection = mysql_connect("", "", "");
  mysql_select_db("database");

  $query = 'insert into news(image) values ('.$im_.')';

    mysql_query($query);  
    $error = mysql_error();
    die($error);

    mysql_close($connection);
?> 
[/PHP]

 where the news.image is of type blob .

 the error i get it : 'You have an error ... near ' and then garbage from
 the image content.

 are there any additional options that one needs to set up in curl or php headers to store images?

plz & thx !!

---

### Post by Bachstelze on 2008-08-13
How about this?

[PHP]$query = "INSERT INTO image VALUES ('$im_')";[/PHP]

---

