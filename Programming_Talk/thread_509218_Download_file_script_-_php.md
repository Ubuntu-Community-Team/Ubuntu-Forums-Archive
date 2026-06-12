---
title: "Download file script - php"
date: 2007-07-25
forum: Programming Talk
---

### Post by adza on 2007-07-25
Hi there, 

        I've been working on a web tool so that i can use my server at home to move files to and from when i'm out and about. I have the uploads working, writing a file path to the database record and saving the file to another location. I also have the download script working, however once the file is downloaded i can't get the page to redirect to another location. The way i've set the file to download is using the header() function... is there a better way to retrieve files? 

Here's my downloading script... 
```

<?php
// always start the session
session_start();
// check if user is logged in
if (!isset($_SESSION['connected']))
	{
	echo "<meta http-equiv='refresh' content='0; url=./index.php'>";
	exit;
	}
$con = mysql_connect("myhost", "myuser", ",mypassword");
if (isset($_REQUEST['ID']))
	{
	$id = $_REQUEST['ID'];
	$query= "SELECT name, type, size, path
		 FROM   works.file_up
		 WHERE  id = '$id';";
	$result=mysql_query($query, $con) or die (mysql_error());
	if (mysql_num_rows($result) == 0)
		{
		echo "No file found - redirecting";
		echo "<meta http-equiv='refresh' content='2; url=./test_welcome.php'>";
		}
	else
		{	
		list($name, $type, $size, $filepath) = mysql_fetch_array($result);
		header("Content-length: $size");
		header("Content-type: $type");
		header("Content-Disposition: attachment; filename=$name");
		readfile($filepath);
		mysql_close($con);
		echo "<meta http-equiv='refresh' content='2; url=./test_welcome.php'>";
		}
	}
?>
<html>
<body>
	<form method="post" type="text">
	<table widt="350" border="1" cellpadding="1" cellspacing="1" class="box">
	<tr>
	<td width="70%">
	File ID:<input name="ID" type="text">
	</td>
	<td width="30%" align="center">
	<input type="submit" class="box" value=" Download ">
	</td>
	</tr>
	</table>
	</form>
</body>
</html>
```

---

### Post by smartbei on 2007-07-25
Have you tried using the header redirect?

Also, you coud use javascript to popup a new window, and set the src of that window to be the file you are trying to download. then, the main page is unaffected and you can do whatever you want with it - redirect, etc.

Why not use something like web ftp...search google, there are several existing solutions.

---

### Post by adza on 2007-07-27
okay, i guess that's cool.... i didn't really want to go and start learning java right now... still dealing with php :P.... what i really want to do is include the above code in a require(download.php) statement in a table cell that also has other cells with upload scripts and the display from the database etc... therefore i want to have one page that serves as the complete app as it were.... if i want to do this, the header statements in this script won't work at all! I have settled (sort of) with a link to this page as displayed above... however, would really like to include this in the table with the upload script... surely php can download a file from the server...?

---

