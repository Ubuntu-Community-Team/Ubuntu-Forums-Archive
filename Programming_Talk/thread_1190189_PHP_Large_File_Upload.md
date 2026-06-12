---
title: "PHP Large File Upload?"
date: 2009-06-17
forum: Programming Talk
---

### Post by Jekshadow on 2009-06-17
Ok, so I have successfully changed my server configuration and php.ini to allow files of any size to be uploaded, but the problem is that the script I'm using (security is NOT an issue, the server only serves my home LAN) checks to see if the file upload and transfer to the final directory is a success. Is there any way to allow it to complete the transfer, and then check if it is successful. I am looking at file uploads of 1-2GB. Here is the part of my script that is important. The rest is just telling the user that it was successful (or not) and MySQL junk.

```

<?php
$furl = rand(1000,9999).$HTTP_POST_FILES['ufile']['name'];
$path= "upload/".$furl;
$fname = $HTTP_POST_FILES['ufile']['name'];
$fsize = $HTTP_POST_FILES['ufile']['size'];
$ftype = $HTTP_POST_FILES['ufile']['type'];
$myname = $_POST['myname'];
if($ufile !=none)
{
[COLOR="Red"]if(copy($HTTP_POST_FILES['ufile']['tmp_name'], $path))[/COLOR]
{
.......

```

---

### Post by Mirge on 2009-06-17
Make sure you up the size in httpd.conf as well... then it's just a matter of using is_uploaded_file(...) and move_uploaded_file(...).

---

### Post by s.fox on 2009-06-18
Hi,

You could try [here ]("http://www.php.net/ftp")for information on how you should use PHP to upload large files as efficiently as possible. I think using the default upload process for files bigger than 2Mb will soon put you at the CPU limit.

-Ash R

---

