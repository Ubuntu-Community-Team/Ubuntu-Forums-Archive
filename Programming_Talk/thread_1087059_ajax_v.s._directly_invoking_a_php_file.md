---
title: "ajax v.s. directly invoking a php file"
date: 2009-03-04
forum: Programming Talk
---

### Post by qmqmqm on 2009-03-04
I have a php file that when is invoked, takes the parameter inside of the url and writes some data to some files on the hard drive.

For example, if I type in the browser "localhost/some_dir/write_to_file.php?param=asdf"
The php file will take the parameter and generate some files on the hard disk

However if I make an ajax call to the same php file using the same url, the ajax session completes and returns, however the php code will not generate the files on the hard disk...

Does anyone know why this is?

Thanks

Tom

---

### Post by viljun on 2009-03-04
Difficult to say... You have the code there to show, haven't you?

Also use error console (Mozilla) or similar to check your javascript code was succesful.

---

### Post by qmqmqm on 2009-03-04
I changed the file name from "export_to_dir.php" to "export.php", but it didnt help...

---

### Post by qmqmqm on 2009-03-04
The php file is as follows.
I would receive the 2 "hi"s and $my_name back from the ajax call in javascript. But the php file doesnt actually do genfiles(...), or at least it was not successful...

But like I said if I call the php file directly from browser, it will work.

Does anyone know why?

```
<?php


$my_name=$_GET["my_name"];


echo "hi";





require_once 'config.php';





$params = get_from_db($connection, $profile_id);




require_once 'file_related.php';

genfiles(params);




echo $my_name;

echo "hi";

?>
```

BTW the "require_once"s are working properly...

---

### Post by viljun on 2009-03-04
Can you show the file that makes the ajax command? Do you get an error message on the browser of browser's error console (mozilla: tools > error console). What else happens when ajax command is executed or does it happen anything at all?

---

### Post by qmqmqm on 2009-03-04
The ajax functions are pretty generic, copied from w2schools i believe...

function ajax_call(url){	
	xmlHttp=GetXmlHttpObject();
	if (xmlHttp==null){
  		alert ("Browser does not support HTTP Request");
  		return;
  	}
  	xmlHttp.onreadystatechange=stateChanged;
	xmlHttp.open("GET",url,true);
	xmlHttp.send(null);
}

function stateChanged() 
{ 
if (xmlHttp.readyState==4 || xmlHttp.readyState=="complete")
 { 
	alert("received: " + xmlHttp.responseText);
 } 
}

function GetXmlHttpObject()
{
var xmlHttp=null;
try
 {
 // Firefox, Opera 8.0+, Safari
 xmlHttp=new XMLHttpRequest();
 }
catch (e)
 {
 // Internet Explorer
 try
  {
  xmlHttp=new ActiveXObject("Msxml2.XMLHTTP");
  }
 catch (e)
  {
  xmlHttp=new ActiveXObject("Microsoft.XMLHTTP");
  }
 }
return xmlHttp;
}

---

### Post by viljun on 2009-03-04
If you got "hi" on your browser when using ajax, there's usually nothing wrong with the ajax call.

There may be encoding problems when using ajax calls. If you use $_REQUEST -or similar things in genfiles() -function you should check the filename is ok.

---

### Post by qmqmqm on 2009-03-04
> **viljun said:**
> If you got "hi" on your browser when using ajax, there's usually nothing wrong with the ajax call.

There may be encoding problems when using ajax calls. If you use $_REQUEST -or similar things in genfiles() -function you should check the filename is ok.

Hi viljun

Could you please explain a bit more?

(I know I use the same way to call other php files and they all work fine. However none of those php files write text files to the hard disk.)

Thanks,

Tom

---

### Post by viljun on 2009-03-04
Could you show the genfiles()-function? Or just try if you can write a file with static file on genfiles().

I mean instead of
$filename = $_REQUEST['filename'];
writetofilefunction($filename);

try first
$filename = 'static';
writetofilefunction($filename);

---

### Post by qmqmqm on 2009-03-04
Hi viljun

Thanks for your reply.

I have changed the php file to the following, and it's the same problem - 
if I open the php file directly, it will generate the "mytest" file.
If I use ajax to call the php file however, the "mytest" file will not be generated.
However I do receive the "hi" back from the ajax call.

Does anyone know why this is?

<?php

$profile_name=$_GET["my_name"];


$file_path = "/mytest";

$file=fopen($file_path, "w");

fwrite($file, "test...");

fclose($file);

echo "hi";

?>

---

### Post by viljun on 2009-03-04
Sorry I'm lost :) The result should be the same.

---

### Post by qmqmqm on 2009-03-04
> **viljun said:**
> Sorry I'm lost :) The result should be the same.

ya i think so too... Thanks anyway viljun!

This is so strange... Must be something wrong.

I am using Windows, IE6, and xampp as web werver on localhost. Don't know if anything else could be causing this...

---

### Post by slavik on 2009-03-04
when using ajax, have you tried looking at apache logs to see if the file ever gets requested and what the return code apache gives for it?

---

### Post by qmqmqm on 2009-03-05
> **slavik said:**
> when using ajax, have you tried looking at apache logs to see if the file ever gets requested and what the return code apache gives for it?

Hi slavik

This is the message I got in the apache access.log file. Does not seem to be any error in error.log...

127.0.0.1 - - [05/Mar/2009:09:33:59 -0500] "GET /export.php?profile_name=Tom_FVG_46R3 HTTP/1.1" 200 30

---

