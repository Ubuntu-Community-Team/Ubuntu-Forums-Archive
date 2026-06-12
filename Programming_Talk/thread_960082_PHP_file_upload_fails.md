---
title: "PHP file upload fails"
date: 2008-10-27
forum: Programming Talk
---

### Post by hessiess on 2008-10-27
Hi, I'm trying to Wright a simple script to upload a file to a server, but for some reason all im managing to get is:

```
Files:Array
(
)


Notice: Undefined index: uploadfile in /srv/http/tests/upload.php on line 14



Notice:  Undefined index:  uploadfile in /srv/http/tests/upload.php on line 17
```

As the $_FILES array seems to be empty I'm guessing something wrong with the server config, which is installed on the same computer. which is running Arch, PHP is working and upload files is on.

upload.html
[PHP]<html>
	<head></head>
	<body>
	<form enctype="multipart/form-data" action="upload.php" method="POST">
	<input type="hidden" name="MAX_FILE_SIZE" value="600000" />
	<input name="uploadfile" type="file" />
	<input type="submit" value="Send File" /> </form> 
	</body>
</html>[/PHP]

upload.php
[PHP]<html>
	<head></head>
	<body>

	<?php
	echo "<pre>\n";

	echo 'Files:';
	print_r($_FILES);

	echo "</pre>\n";

	$uploaddir = 'uploads/';
	$uploadfile = $uploaddir . basename($_FILES['uploadfile']['name']);

	echo '<pre>';
	if (move_uploaded_file($_FILES['uploadfile']['tmp_name'], $uploadfile)) 
	{
	    echo "worked\n";
	} 
	else
	{
	    echo "error\n";
	}
	echo "</pre>";
	?>
	</body>
</html>[/PHP]

---

### Post by Porpoise on 2008-10-27
> **hessiess said:**
> Hi, I'm trying to Wright a simple script to upload a file to a server, but for some reason all im managing to get is:

```
Files:Array
(
)


Notice: Undefined index: uploadfile in /srv/http/tests/upload.php on line 14



Notice:  Undefined index:  uploadfile in /srv/http/tests/upload.php on line 17
```As the $_FILES array seems to be empty I'm guessing something wrong with the server config, which is installed on the same computer. which is running Arch, PHP is working and upload files is on.

upload.html
[php]<html>
    <head></head>
    <body>
    <form enctype="multipart/form-data" action="upload.php" method="POST">
    <input type="hidden" name="MAX_FILE_SIZE" value="600000" />
    <input name="uploadfile" type="file" />
    <input type="submit" value="Send File" /> </form> 
    </body>
</html>[/php]upload.php
[php]<html>
    <head></head>
    <body>

    <?php
    echo "<pre>\n";

    echo 'Files:';
    print_r($_FILES);

    echo "</pre>\n";

    $uploaddir = 'uploads/';
    $uploadfile = $uploaddir . basename($_FILES['uploadfile']['name']);

    echo '<pre>';
    if (move_uploaded_file($_FILES['uploadfile']['tmp_name'], $uploadfile)) 
    {
        echo "worked\n";
    } 
    else
    {
        echo "error\n";
    }
    echo "</pre>";
    ?>
    </body>
</html>[/php]


You may be better off posting this in a PHP forum rather than here, as you are more likely to get responses from people who know PHP (as it's a PHP question, not a Ubuntu question). 

One thing that's obvious though, is that the $_FILES variable is not getting 'uploadfile' from the form input, so the first thing I would try is eliminating the XML closing tags ( /> ) and replace them with valid HTML closing tags ( > )

---

