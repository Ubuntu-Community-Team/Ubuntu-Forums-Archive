---
title: "Uploading an image using PHP and storing the location in a database"
date: 2010-01-13
forum: Programming Talk
---

### Post by dmillerw on 2010-01-13
Basically I'm trying to get a basic upload form, that allows images only and uploads them to a folder on my server, at the same time I'm trying to have the location of the image stored in a MySQL database for later use.

I'd just use BLOB and whatnot, but I tend to mess things up on my server, and after reading about problems with restoring databases with large files, I felt this would be easier.

[PHP]        <script type="text/javascript">
            function displayForm(c){
                if(c.id == "1"){
                    document.getElementById("form1").style.visibility='visible';
                    document.getElementById("form2").style.visibility='hidden';
                }
                else if(c.id =="2"){
                    document.getElementById("form1").style.visibility='hidden';
                    document.getElementById("form2").style.visibility='visible';
                }
                else{
                }
            
            }        
        </script>  

<html>
<body>
<form action="insert.php" method="post">
First name: <input type="text" name="FName" />
<br>
Last name: <input type="text" name="LName" />
<br>
Username: <input type="text" name="UName" />
<br>
Student ID: <input type="text" name="StuID" id="form1"/>
<br>
Password: <input type="text" name="PWord" id="form2" style='visibility:hidden;'/>
<br>
Picture:
<input type="file" name="userfile" id="file"> <br />
Category:
<br>
<input type="radio" name=Cat onclick="displayForm(this)" value="School" id="1" default>School
<br>
<input type="radio" name=Cat onclick="displayForm(this)" value="Facebook" id="2">Facebook
<br>
<input type="radio" name=Cat onclick="displayForm(this)" value="MySpace" id="2">MySpace
<br>
<input type="radio" name=Cat onclick="displayForm(this)" value="Other" id="2">Other
<br>
<input type="submit" value="Update Database" />
</form>
</body>
</html> [/PHP]

Thats the upload page, which, among other things just has a very basic upload box.

[PHP]<?php
include"upload.php";

$Password2 = substr ($_POST['LName'], 0, 2).substr ($_POST['StuID'], 2);
$Password = $query = strtolower($Password2); 
$con = mysql_connect("localhost","root","passoword");
if (!$con)
  {
  die('Could not connect: ' . mysql_error());
  }

mysql_select_db("pwordlist", $con);

$sql="INSERT INTO PWordTable (Cat, FName, LName, UName, PWord, StuID)
VALUES
('$_POST[Cat]','$_POST[FName]','$_POST[LName]','$_POST[UName]','$Password','$_POST[StuID]')";

if (!mysql_query($sql,$con))
  {
  die('Error: ' . mysql_error());
  }
echo "$_POST[FName] has been added to the database";


mysql_close($con)
?> [/PHP]

Thats obviously whats storing the data, I need it to also upload the file and store the location.

I've been attempting different methods, and got uploading to work, but just can't figure out how to store the location.

Thanks for any help

---

### Post by Hellkeepa on 2010-01-13
HELLo!

First of all, I cleaned up your HTML form for you. Quite a few issues there, non-unique and non-conforming IDs for one thing. All IDs must be unique, and start with a letter. I highly recommend a read through the HTML specs, to iron out details like this and which tags are allowed and which ones are required within other tags.
Here's the cleaned up code: [http://pastebin.com/f39c55ed](http://pastebin.com/f39c55ed)

Now, onto the PHP script...
First of all I notice a glaring lack of security, along with a [certain familiarity with the scripts functionality and naming convention](http://ubuntuforums.org/showthread.php?t=1358960). (And lo and behold, it's the same person. :-P )
To get the upload working, I recommend a thorough look at "[move_uploaded_file ()](php.net/move_uploaded_file)", and its associated array "[$_FILES](php.net/_FILES)". Do remember to validate everything, I have written a couple of posts on this here before. I recommend a search for them. ;-)

In any case, I also highly recommend reading through [this thread](http://ubuntuforums.org/showthread.php?t=1357034), which is a nice thread to get started on database security on.

Happy codin'!

---

