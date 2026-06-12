---
title: "PHP Sockets"
date: 2007-06-25
forum: Programming Talk
---

### Post by hammo on 2007-06-25
Hello Everyone,

I am having some problems writing a php script that uses socket functions. Basically I:

 - Have created a telnet client in PERL that receives the temperature of a sensor attached to the back of a server using a serial port.
 - Created a server that receives the data from the telnet client (Also in PERL). Now this server has two functions:
     - INSERT: If a connection from a client prints the string "insert", then the server inserts the value of the insert data into a string.
     - VIEW: If a connection is received from a client and the client prints the string 'view', then the server prints the content of the string to client.

Now, I have found several php socket connection type scripts. Here is one that I wrote myself based on what I found;

<?php

$socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
$connection = socket_connect($socket, 'server', 15905);
socket_write($socket, "view\r");
while ($data = socket_read($socket,2046, PHP_NORMAL_READ);

{

	echo $data;

}
socket_close($socket);

?>

Now for some reason, when I use this script I get an error that returns something along the lines of 'No data to read on socket[0]'. Now I have tested it using telnet. It all works on both Linux and Windows. I'm pretty sure that's all the info that I really have.

Thanks and Regards,

Adam

---

### Post by leibowitz on 2007-06-25
I never used sockets before with PHP, but apparently you need to Create, Bind, Listen, Acppet, and then Read. I'm not sure about the last one.

Inspired from [http://be2.php.net/manual/en/function.socket-accept.php](http://be2.php.net/manual/en/function.socket-accept.php)
```
<?
$address = "server";
$port = "4545"
$socket = socket_create(AF_INET,SOCK_STREAM,SOL_TCP);
socket_bind($socket,$address,$port);
socket_listen($socket);

$accepted = socket_accept($socket);

if($accepted)
{
  $data = socket_read($socket,2046, PHP_NORMAL_READ);
  echo $data;
  socket_close($socket);

}

?>
```

Please adapt the Read part, as I'm not sure how to stop the loop properly without error.

---

### Post by aks44 on 2007-06-25
If you're writing a PHP client (that's what I understood from your post, but leibowitz made me doubt ;)), using **fsockopen** and the standard file functions **feof** / **fread** / **fwrite** / **fclose** will be more than enough.

Something like :

[PHP]$sock = fsockopen('server',$port);
if ($sock)
{
  fwrite($sock,'view\n');
  $data = '';
  while (!feof($sock))
    $data .= fread($sock,4096);
  fclose($sock);
  echo $data;
}
else
  die('painfully');[/PHP]

---

