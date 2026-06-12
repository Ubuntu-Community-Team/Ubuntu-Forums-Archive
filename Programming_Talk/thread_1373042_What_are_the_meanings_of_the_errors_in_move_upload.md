---
title: "What are the meanings of the errors in move_uploaded_file?"
date: 2010-01-05
forum: Programming Talk
---

### Post by kapi on 2010-01-05
Am working on a simple file upload function in php and can't seem to find anything related to the error meanings.

For instance I have error 1 when trying to upload a song to a folder.

I haven't restricted the upload size as yet and wondered if anyone knows. 

Php.net doesn't say much except it is boolean and returns false or true. fair enough I suppose - it works or doesn't but I wanted a little more feed back as to why.

If you can help I'd be grateful

Thanks

---

### Post by lolzwut on 2010-01-05
First of all post the code so we can analyze the actual code.

Second make sure you use a writable directory.

---

### Post by warfacegod on 2010-01-05
I was under the impression that error 1 usually means that the hard drive is full.

---

### Post by Hellkeepa on 2010-01-05
HELLo!

You do realize that "move_uploaded_file ()" returns boolean TRUE on success, which equates to 1? Unless you use "var_dump ()" you won't be told the type of the variable, and it'll just display the integers 1 or 0 instead of "true" or "false" when printing the value.

Happy codin'!

---

### Post by kapi on 2010-01-05
<?php

$name = $_FILES["myFile"]["name"];
$type = $_FILES["myFile"]["type"];
$size = $_FILES["myFile"]["size"];// output in bytes -  1 million bytes is 1 megabyte
$tmp_name = $_FILES["myFile"]["tmp_name"];
$error = $_FILES["myFile"]["error"];

if($error >0)
{
	switch($error)
	{
		case 1:
			die("<p> The file is bigger than this PHP installation allows</p>");
        break;

		case 2:
			die("<p> The file is bigger than this form allows</p>");
        break;

		case 3:
			die("<p> Only part of the file was uploaded</p>");
        break;
		
		case 4:
			die("<p> No file was uploaded</p>");
        break;

	}
}
else
{

	if (($_FILES["file"]["type"] == "image/gif")
	|| ($_FILES["file"]["type"] == "image/jpeg")
	|| ($_FILES["file"]["type"] == "image/pjpeg"))
	
	{
		die("Sorry that format is not allowed!");
	}
	else
	{
		move_uploaded_file($tmp_name,"uploaded/".$name);
		echo "upload complete.";
	}
}
?>

---

### Post by Hellkeepa on 2010-01-05
HELLo!

Except a complete lack of security, and bad usage of blacklisting instead of white listing, I don't see any problems here. Care to explain where you see this "error value", and what you do when you get it?

Also, no point in having an else-block after a "die()" or "return" statement. The script will end at that point anyway, ensuring that all following code will only be executed if the if-test fails.

PS: Please use the [****php][/php] tags when posting PHP code, makes it that much more readable.

Happy codin'!

---

### Post by hessiess on 2010-01-05
Assuming you are not running PHP as the owner of the upload directory (i.e. via suexec) it will probably need to be chmod 777 otherwise PHP would now have permission to write to the directory.

---

### Post by Reiger on 2010-01-05
Please use code blocks; and also consider that the move_uploaded_file() function does not use meaningful errors other than success/failure.

[php]
if(move_uploaded_file($tmp, $path)) {
  echo "Success!";
}
else {
  echo "Failure!";
}
[/php]

The PHP.net $_FILES (superglobal) documentation should cover this topic (as well).

---

### Post by kapi on 2010-01-05
Thanks for the replies. 

As you can tell I'm just getting to grips with php so I apologise for the lack of knowledge, presentation etc.

I can upload txt documents, jpegs, and png images but when I tried to see if I could simply copy a song from the music folder to the destination folder (var/www/etc) it gave me error 1.

I have permissions set correctly otherwise I wouldn't be able to move anything.

I just wondered why I was getting the error as I deliberately didn't specify file type restrictions to begin with. The music file is only 4mb.

I appreciate your help and advice and don't want to appear ignorant but when you mentioned white and black listing what does that mean?

---

### Post by lolzwut on 2010-01-05
Depending on your PHP instillation sometimes it automatically sets file upload size limits. You can check your phpinfo to find out

[PHP]<?php
phpinfo();
?>[/PHP]

or if you don't wanna bother looking just add to your form:

```
<input type="hidden" name="MAX_FILE_SIZE" value="999999999999999999999" />
```

just so we can rule out if the file is too big.

good luck

---

### Post by kapi on 2010-01-05
You're correct!

the file size is set to 50 which I presume is bytes. will try and work out how to change the defaults

Thanks again for the help.

---

### Post by Hellkeepa on 2010-01-05
HELLo!

**lolzwut**: That input-tag is only for the browser, PHP still uses the directive in the "php.ini". Be adviced that the "max_post_size" also affects the size of the files that can be posted, since they're a part of the POST-data.

**kapi**: When you say "error 1", I reckon you're referring to the status in the $_FILES array. More specifically, the number you get from here:
[php]$_FILES["myFile"]["error"];[/php]
If this is indeed the case, then this has nothing to do with "move_uploaded_file ()". In this case, **Reiger** has answered your question in the last line of his post.

Also, assuming things are usually a recipe for errors. I Highly recommend you to read about this particular directive in the manual, or even in the INI file itself.

Happy codin'!

---

### Post by kapi on 2010-01-05
Thank you very much for the feed back,

it's appreciated.

:-)

---

