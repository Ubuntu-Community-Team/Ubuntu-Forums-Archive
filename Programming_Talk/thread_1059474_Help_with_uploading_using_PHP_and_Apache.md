---
title: "Help with uploading using PHP and Apache"
date: 2009-02-03
forum: Programming Talk
---

### Post by Retaliation on 2009-02-03
Hi everyone, Im running an Apache server at my house for me and my friends to use, but lately Ive been having some trouble.

I have a basic php upload script I found on the internet, since I have nearly no knowledge of php, that I use for uploading various types of files to my server.

Now I cannot upload any file that is above ~5mb without the upload failing. Could this have anything to do with the script being on my ssl server?

 For most files it says "upload failed" then gives me debug info, such as size, name, type and error. for error it gives 0 and all other debug info is normal, but the upload still does not work. For some files, it doesnt even give file size or aything but the name, and gives a error code of 1.

Im using apache2.0 and PHP5 btw.

here are my upload scripts...

[PHP]<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
	<head>
	<title></title>
	</head>
	<body bgcolor ="black">	
	<form enctype="multipart/form-data" action="uploader.php" method="POST">
	<input type="hidden" name="MAX_FILE_SIZE" value="10000000" />
	<input name="uploadedfile" type="file" /><br />
	<input type="submit" value="Upload" />
	</form>
	</body>
</html>[/PHP]

and the other one...

[PHP]<?php

$uploaddir = 'Uploads/';
$uploadfile = $uploaddir . basename($_FILES['userfile']['name']);

echo '<pre>';
if (move_uploaded_file($_FILES['userfile']['tmp_name'], $uploadfile)) {
    echo "File is valid, and was successfully uploaded.\n";
} else {
    echo "File upload failed.\n";
}

echo 'Here is some debugging info:';
print_r($_FILES);

print "</pre>";

?>[/PHP]

Ive been trying to find a solution to this for a couple days now, even tried other upload scripts, but for nothing.

thanks in advance

---

### Post by Reiger on 2009-02-04
Ehrm: two things:
(1) Does the directory Uploads/ reside under /var/www ? Does it have appropiate file permissions?
(2) Why do you call your form field "uploadedfile" when your script expects that to be "userfile" ?

(I see you read the file upload tutorial on PHP.net, but you must have missed the bit about how field names affect the keys to the $_FILES array.)

---

### Post by tturrisi on 2009-02-04
Where is the php code that processes this input:
    <input type="hidden" name="MAX_FILE_SIZE" value="10000000" />

---

### Post by Retaliation on 2009-02-08
Thanks for the help, but I've just decided to make an FTP server to simplify things and for my own enjoyment :). Thanks anyway though!

---

