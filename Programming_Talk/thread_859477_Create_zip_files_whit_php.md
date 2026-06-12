---
title: "Create zip files whit php"
date: 2008-07-14
forum: Programming Talk
---

### Post by irfan798 on 2008-07-14
I wonder about could i create zip files in php like this image file.
If you run this php create an image and its not html file, its a png file and user can download it

[PHP]<?php
header("Content-type: image/png");
$im = @imagecreate(110, 20)
    or die("Cannot Initialize new GD image stream");
$background_color = imagecolorallocate($im, 0, 0, 0);
$text_color = imagecolorallocate($im, 233, 14, 91);
imagestring($im, 1, 5, 5,  "A Simple Text String", $text_color);
imagepng($im);
imagedestroy($im);
?>[/PHP]
I want zip something then give it to users but &#305; dont want save it, after finish users donwload it destroy it seflf like this and my hdd have more spaces. 
I tried this but it wasnt work
[PHP]<?php
header("Content-type: application/zip");

$zip = new ZipArchive();

$zip->addFile("a.php");

$zip->close();


?>
[/PHP]
And this save zip file
[PHP]<?php

$yol="/opt/lampp/htdocs/psmatlib/".$_GET['ziple'];
$zip = new ZipArchive();

if ($zip->open("abc.zip", ziparchive::CREATE)!==TRUE) {exit(" acilamadi\n");}


$zip->addFile("nofile.jpg");

$zip->close();
chmod($filename, 0777);

?>[/PHP]

You can write your alternate ideas:confused:
Thanks for your answers..

---

### Post by drubin on 2008-07-15
An option using pear.
[http://www.phpit.net/article/creating-zip-tar-archives-dynamically-php/](http://www.phpit.net/article/creating-zip-tar-archives-dynamically-php/) 

[http://www.web-development-blog.com/archives/tutorial-create-a-zip-file-from-folders-on-the-fly/](http://www.web-development-blog.com/archives/tutorial-create-a-zip-file-from-folders-on-the-fly/)

---

### Post by irfan798 on 2008-10-22
Sory I haven't got enough time. And I forgot to write here...

Okay the key point is **file_get_contents()** function.
That function will give you the source of your material.

See [http://tr2.php.net/manual/en/function.file-get-contents.php]("http://tr2.php.net/manual/en/function.file-get-contents.php")

[PHP]
header("Content-type: application/zip"); //Say to browser "This is a zip file"

header('Content-Disposition: attachment; filename="users_will_see_this.zip"');




//Create a new zip file
$zipobject = new ZipArchive();
$zipobject->open("test.zip", ZipArchive::OVERWRITE);
$zipobject->addFile("1.jpg");
$zipobject->addFile("2.jpg");
$zipobject->addFile("3.jpg");
$zipobject->addFile("4.jpg");
$zipobject->addFile("5.jpg");
$zipobject->addFile("6.jpg");
$zipobject->close();

echo file_get_contents("test.zip"); //Write file in string format

unlink("test.zip"); //Delete the file [/PHP]

When you write it as a php and execute, program will do it this order

[LIST=1]
[*]Browser! This is a zip file
[*]Create a new zip file
[*]Put some images in it
[*]Close the zip file
[*]**Read the zip file as a string and write it.**
[*]Delete the zip file
[*]Page is now ready
[/LIST]

You can do it with any file format.
Good coding ;)

---

### Post by drubin on 2008-10-22
> **irfan798 said:**
> 

[PHP]
echo file_get_contents("test.zip"); //Write file in string format

 [/PHP]


Another option is [fpassthru]("www.php.net/function.fpassthru")

---

