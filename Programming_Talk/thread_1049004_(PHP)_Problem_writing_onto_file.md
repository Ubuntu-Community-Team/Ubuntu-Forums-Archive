---
title: "(PHP) Problem writing onto file"
date: 2009-01-24
forum: Programming Talk
---

### Post by IsolatedEarthling on 2009-01-24
This forum code is supposed to write the topic, name and message onto a txt file. However, the text file remains empty after i submitted the message. Pls help. Thnx in advanced.
[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<title>Post New Message</title>
<style type="text/css">
<!--
#form1 table tr td h1 strong {
	color: #FFF;
}
#form1 table {
	color: #000;
}
body {
	background-color: #000;
}
#form1 table tr td p {
	color: #CCC;
}
td {
	color: #FFF;
}
a:link {
	color: #FFF;
	text-decoration: none;
}
a:visited {
	text-decoration: none;
	color: #FFF;
}
a:hover {
	text-decoration: underline;
	color: #FFF;
}
a:active {
	text-decoration: none;
	color: #FFF;
}
body,td,th {
	color: #CCC;
}
-->
</style>
</head>

<body>
<form id="form1" name="form1" method="post" action="">
  <p>&nbsp;</p>
  <table width="574" border="0" align="center">
    <tr>
      <td height="28" colspan="2" bgcolor="#000000"><h1><strong>POST NEW MESSAGE</strong>      </h1>
      <hr /></td>
    </tr>
    <tr>
      <td width="369" height="28">Topic: 
        <label>
          <input name="txtTopic" size="50" type="text" id="txtTopic" value="" />
      </label></td>
      <td width="195">Name: 
        <label>
          <input type="text" name="txtName" id="txtName" />
      </label></td>
    </tr>
    <tr>
      <td height="843" colspan="2" align="left" valign="top"><p>Message:</p>
      <p>
        <label>
          <textarea name="txtMessage" id="txtMessage" cols="90" rows="15"></textarea>
          <input type="submit" name="btnPostmessage" id="btnPostmessage" value="Post Message" />
        </label>
      </p>
      <hr />
      <p><a href="forum.php">Return to Forum page</a></p>
      <p><a href="index.html">Return to homepage</a></p></td>
    </tr>
  </table>
</form>
<?php
$topic=$_POST("txtTopic");
$name=$_POST("txtName");
$message=$_POST("txtMessage");
$filename= "messages.txt";
$output= "Topic:".$topic."\t"."Name: ".$name."\t"."Message: ".$message."\n";

$fh=fopen($filename,"a");
fwrite($fh,$output);
fclose($fh);
?>
</body>
</html>[/HTML]

---

### Post by Canuckelhead on 2009-01-24
How are you running the PHP?  Apache?
If so it's likely a permissions issue you're dealing with...

If the txt file isn't owned by Apache you'll need to change the permissions...

chown apache myFolder

and set the permissions to:

drwxr-xr-x

---

### Post by mssever on 2009-01-24
You aren't checking the return value of fopen, so you're probably missing any error messages. It's been a long time since I've manipulated files in PHP, so I don't remember how it reports such errors.

Also, it's quite likely that PHP doesn't have permission to write the file. Make sure that the user your server runs as has the appropriate write access.

---

### Post by Canuckelhead on 2009-01-24
I think the user t should actually be... "www-data" and not "apache"

---

### Post by Reiger on 2009-01-24
First of all: your form action attribute does not point to your script...?
So where exactly is any data uploaded to, is your script actually executed at all?

Now about the PHP code itself:
Failure to write etc. should be reported as warnings. And I'm actually surprised to see the $_POST() notation work, AFAIK it ought to return FATAL parsing errors (unexpected '(') as the $_POST superglobal is an associative array (or at least accessible as such). If you want to see anything PHP complains about, make sure your script (stack) *does* return output (which means there's a socket for the warnings to be written to) like this:

[php]
<?php
$topic=$_POST["txtTopic"];
$name=$_POST["txtName"];
$message=$_POST["txtMessage"];
$filename= "messages.txt";
$output= "Topic:".$topic."\t"."Name: ".$name."\t"."Message: ".$message.PHP_EOL; /* defined constant, will work anywhere PHP works... */
if(file_put_contents($filename,$message,FILE_APPEND)) /* See the manual */
  echo "Succes!";
else
  echo "Fail!";
?>
[/php]
Of course, you could check the server/PHP logs... ;)

---

