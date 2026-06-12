---
title: "upload image problem"
date: 2008-06-23
forum: Programming Talk
---

### Post by Miben on 2008-06-23
Hi, I'm using ubuntu.I face problem with image uploading in web development.I run my web application files in localhost. All files locate in var/www. I also create a folder named "uploads" in my document. During uploading image, it supposes to move the uploaded image into "uploads".But, it wont. The Error show was "uploads file does not exist in var/www".Anyone can show me the way to solve this problem?Thanks...!

---

### Post by henchman on 2008-06-24
Sorry, but could you please describe your problem more detailed:

- eg. do you use ftp to upload?
- a scripting language like PHP? 

If its for example PHP, please check your folder permissions. Try setting it to 777 just for testing purposes and if this works, set it properly :) The user under which apache/php runs needs to have writing permissions. If this doesn't work, please supply your code.

Cheers. Bye.

---

### Post by Miben on 2008-06-24
As i know var/www in ubuntu is a root directories.Meaning that only the default user can access to itl.And var/www also a default localhost.After i write my upload.php, i need to copy the file into var/www/shopping directories for the purpose to test in browser(localhost).
**shopping is the directories i create using sudo command from terminal.When i test with browser, always give warning permission denied.Actually, i want to move the image uploaded into a folder "uploads" in home directories.But, i cant figure out the right way to specified the path.I had try in many ways but not working.Any suggestion???

code:upload.php

<?php
$uploadDir = $_SERVER['DOCUMENT_ROOT'] . "uploads/";

if ((($_FILES["file"]["type"] == "image/gif")
|| ($_FILES["file"]["type"] == "image/jpeg")
|| ($_FILES["file"]["type"] == "image/pjpeg"))
&& ($_FILES["file"]["size"] < 20000))
  {
  if ($_FILES["file"]["error"] > 0)
    {
    echo "Return Code: " . $_FILES["file"]["error"] . "<br />";
    }
  else
    {
    echo "Upload: " . $_FILES["file"]["name"] . "<br />";
    echo "Type: " . $_FILES["file"]["type"] . "<br />";
    echo "Size: " . ($_FILES["file"]["size"] / 1024) . " Kb<br />";
    echo "Temp file: " . $_FILES["file"]["tmp_name"] . "<br />";

    if (file_exists("upload/" . $_FILES["file"]["name"]))
      {
      echo $_FILES["file"]["name"] . " already exists. ";
      }
    else
      {
     move_uploaded_file($_FILES["file"]["tmp_name"],
      "$uploadDir". $_FILES["file"]["name"]);
      echo "Stored in: " . "Uploads" . $_FILES["file"]["name"];
      }
    }
  }
else
  {
  echo "Invalid file";
  }
?>

<html>
<body>

<form action="upload.php" method="post" enctype="multipart/form-data">
<label for="file">Filename:</label>
<input type="file" name="file" id="file" /> 
<br />
<input type="submit" name="submit" value="Submit" />
</form>

</body>
</html>

---

### Post by dexter.deepak on 2008-06-24
i havent tried php, but from my jsp knowledge, i could guess, you can try : (supposing the document root is /var/www)
$uploadDir = $_SERVER['DOCUMENT_ROOT'] . "../../home/user/uploads/";

the home dir. should have proper write permissions for others.

---

### Post by cpetercarter on 2008-06-24
I have found that it is easier to deal with problems of ownership and permissions if I create a "www" diectory in my home/[username] directory, and use that as the default "localhost" location. [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP"), the section on virtual hosts, explains the very simple changes needed to do this.

---

### Post by henchman on 2008-06-24
> If its for example PHP, please check your folder permissions. Try setting it to 777 just for testing purposes and if this works, set it properly :) The user under which apache/php runs needs to have writing permissions. If this doesn't work, please supply your code.

Have you tried this on your ~/uploads directory? Iam pretty sure it's this problem.

edit: 

[chmod]("http://www.manpagez.com/man/1/chmod/") works this way: 

```
chmod mode file
```

where mode is eg: 777 ( read/write-permission for everyone ) and file is your directory, eg: /homes/Miben/uploads

---

### Post by Miben on 2008-06-24
Thanks!! It works after i change the permissions to 777.But, the image stored cannot be viewed by directly click on it. What should i do?

---

### Post by henchman on 2008-06-24
Please remember to change the rights of the directory to a more save value as described above :)

Do you mean the image is not being opened by your image program when you open it by double-clicking? This is strange... sorry, dont't know what happened there...

---

