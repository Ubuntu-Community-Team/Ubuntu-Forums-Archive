---
title: "PHP upload script"
date: 2009-12-21
forum: Programming Talk
---

### Post by matmatmat on 2009-12-21
I am trying to create an upload script:

Form:
[PHP]
<?php
require_once("include/db.php");

echo '<div style="width:790px;min-height:700px;margin:auto;background:white">';
include_once("include/header.php");
include_once("include/navbar.php");

session_start();

if(!isset($_SESSION['valid_user']) || $_SESSION['valid_user'] != "admin"){
        echo '<h1>Error</h1>';
        echo 'You do not have the required permissions to see this page -- please go back';
}else{
?>
<h1>Add user</h1>
<form enctype="multipart/form-data" action="adduser.php" method="post">
<table>
<tr><td>Username: </td><td><input  type="text" name="user" /></td></tr>
<tr><td>Password: </td><td><input type="password" name="passwrd" /></td></tr>
<tr><td>Confim Password: </td><td><input type="password" name="passwrd2" /></td></tr>
<input type="hidden" name="MAX_FILE_SIZE" value="9000000" />
<tr><td>Image: </td><td><input name="file" type="file" /></td></tr>
</table>
<input type="submit" value="Submit" />
</form>
<?php
}
?>

[/PHP]

Backend (adduser.php):
[PHP]
<?php                                                   
require_once("include/db.php");                         

echo '<div style="width:790px;min-height:700px;margin:auto;background:white">';
include_once("include/header.php");                                            
include_once("include/navbar.php");                                            

$user  = $_POST['user'];
$pass  = $_POST['passwrd'];                                                                                                                                  
$pass2 = $_POST['passwrd2'];                                                                                                                                 
$file  = $_POST['file'];                                                                                                                                     
                                                                                                                                                             
if(!$user || !$pass || !$pass2 ){                                                                                                                            
        echo '<h1>Error</h1>';
        echo 'Please go back and fill in all required fields';
        exit;
}else{
        echo '<h1>Adding user</h1>';
        echo 'Uploading file...<br />';

        if ($_FILES['file']['error']){
                echo '<b>ERROR UPLOADING FILE </b>';
                exit;
        }

        $upfile = 'images/users/'.$user;

        if (is_uploaded_file($_FILES['file']['tmpname'])){
                move_uploaded_file($FILES['file']['tmpname'], $upfile);
        }else{
                echo '<b>ERROR -- FILE NOT UPLOADED</b>';
        }
}
[/PHP]

When run it says 'ERROR -- FILE NOT UPLOADED', can anyone tell me what the cause of this might be?

---

### Post by Hellkeepa on 2009-12-21
HELLo!

Well.. Ignoring the complete lack of security, the error is quite simple. You'd found it yourself, had you dumped the data from the "$_FILES" array.

Also taken the liberty of cleaning up your code a bit, to show you a slightly better coding style. A style that allows you to really take advantage of PHP, since all processing is done prior to anything being sent to the browser:
[http://pastebin.com/d39feb35c](http://pastebin.com/d39feb35c)
Note that it still needs some more security, especially on the part of the file management.

Here's the link to my validation functions: [http://norskwebforum.no/pastebin/7609](http://norskwebforum.no/pastebin/7609)

Happy codin'!

---

### Post by matmatmat on 2009-12-21
What is the error -- I can't see what it is from the code?

---

### Post by v8YKxgHe on 2009-12-21
If you had been coding with the correct error reporting, and display errors on - you'd see. 

Either edit your php.ini file to change 'error_reporting' to 'E_ALL | E_STRICT' and 'display_errors' to 'On', or add top of your script:

[php]<?php ini_set('display_errors', true); error_reporting(E_ALL | E_STRICT); ?>[/php]
Then watch as the PHP notices come flooding in. And as hellkepa said, as it stands anyone could upload any file to any directory your script has permission to.

---

### Post by Hellkeepa on 2009-12-22
HELLo!

Just noticed there were in fact two errors, one of which I copied in my version as well. The second error being a typo in the "move_uploaded_file()" statement, missing an underscore in the variable name. Not that it matters much, yet, seeing as the first error stops this line from being executed at all.

**matmatmat**: I'll give you another hint. Add "var_dump ($_FILES);" just before the error message you get, and compare its output to the source code.

Happy codin'!

---

### Post by matmatmat on 2009-12-22
Thanks everyone!

---

