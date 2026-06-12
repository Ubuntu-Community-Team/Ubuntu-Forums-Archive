---
title: "Unknown column '$name' in 'field list'"
date: 2009-09-26
forum: Programming Talk
---

### Post by Eviltechie on 2009-09-26
I'm trying to make a php script to insert some data into a table, but it doesn't seem to be working.

```
<?php
$name = $_POST['name'];
$email = $_POST['email'];
$song = $_POST['song'];
$artist = $_POST['artist'];
$client_ip = $_SERVER['REMOTE_ADDR'];

$name = mysql_real_escape_string($name);
$email = mysql_real_escape_string($email);
$song = mysql_real_escape_string($song);
$artist = mysql_real_escape_string($artist);


mysql_query('INSERT INTO request (name, email, song_name, artist_name, ip_address) VALUES($name, $email, $song, $artist, $client_ip) ') or die(mysql_error());


echo "Request succesfully submitted";
?>
```

The mysql query is the offending line of code.

You can view the html for the form here. [http://trilug.pastebin.com/f4322521b](http://trilug.pastebin.com/f4322521b)

---

### Post by januzi on 2009-09-26
echo "VALUES($name, $email, $song, $artist, $client_ip)" ;
echo 'VALUES($name, $email, $song, $artist, $client_ip)' ; 

And You should put values into ` ` or ' ' (mysql doesn't like: values( some text, email@domain, 1, 1, 127.0.0.1) )

---

### Post by credobyte on 2009-09-26
[php]mysql_query("INSERT INTO request (name, email, song_name, artist_name, ip_address) VALUES ('$name', '$email', '$song', '$artist', '$client_ip')") or die(mysql_error());
[/php]P.S. - mysql error means that it can't find a column <name> ( not related to $_POST ).

---

### Post by korvirlol on 2009-09-27
youll get a whitespace error for doing the above.

[COLOR=#000000][COLOR=#0000BB][/COLOR][/COLOR]you have to encapsulate your variables in the string in 1 of 2 ways (only 2 i know)
```

mysql_query("insert into table (col1, col2, col3) values ('".$var1."', '".$var2."', '".$var3."')");
```

or 
```

mysql_query("insert into table (col1, col2, col3) values ('{$var1}', '{$var2}', '{$var3}')"); 
```

---

