---
title: "php uploading problem on ubuntu"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by toniknik1982 on 2011-10-17
I'm using Ubuntu 11.04 Desktop, I just installed LAMP on it because I'm going to use this as my test web server. I have problem on uploading file (usually .jpg) using PHP, file appears to be uploaded successfully but when i try to view my "upload" folder file isn't there. I modified the document root location in apache2 it is "/home/guesthere/php_practice" and the "upload" folder is a sub-folder of php_practice. Here's my code:

[U][COLOR=Red]index.html[/COLOR]
[/U]
<html> 
<head><title>Main</title></head> 
<body> 
<form action = 'Upload.php' method = 'post' enctype = 'multipart/form-data'> 
<input type = 'file' name = 'fUpload'> 
<br> 
<br> 
<input type = 'submit' name = "Submit" value = 'Submit'> 
</form> 
</body> 
</html> 


[COLOR=Red]_Upload.php_[/COLOR]

<html> 
<head><title>To_Upload</title></head> 
<body> 
<?php 
$name = $_FILES['fUpload']['name']; 
$tmp = $_FILES['fUpload']['tmp_name']; 
$folder = "upload/"; 

//to view the file name
echo $name . "<br>"; 

//to view the actual location in tmp folder
echo $tmp . "<br>"; 

move_uploaded_file($tmp,$folder); 

echo (is_uploaded_file($_FILES['fUpload']['tmp_name'])); 

</body> 
</html> 


[SIZE=3]Here's the Output:[/SIZE]

[SIZE=3][B]test1.jpg
/tmp/phpCv1asD
1
[/B][/SIZE]

Please help......

---

