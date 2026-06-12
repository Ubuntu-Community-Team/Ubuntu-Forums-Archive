---
title: "Cannot upload files using PHP5 &amp; Apache2"
date: 2008-05-08
forum: Programming Talk
---

### Post by mikemosher on 2008-05-08
Hey everybody, 

I am working on uploading files.  I know it should be easy, but it just isn't working for me.  I don't get any errors or problems, and I see the file name being uploaded in the GET parameters, but when I check $_FILES['uploaded_image'] there is nothing.  

I have checked the php.ini:
file_uploads = On
upload_max_filesize = 2M
post_max_size = 8M

Here is test html:


<form id='add_file' action='index.php' method='get' enctype='multipart/form-data'>
									FILE:				
<input type='file' name='image0' size='28'>

<a href='#' onClick=\"document.getElementById('add_file').submit();\"><b>Add File</b></a>
</form>



Here's PHP example code:

if ($_FILES["image0"]["name"] != '') {
	if ((($_FILES["image0"]["type"] == "image/gif") || ($_FILES["image0"]["type"] == "image/jpeg") || ($_FILES["image0"]["type"] == "image/pjpeg")) && ($_FILES["image0"]["size"] < 1000000)) {
	if ($_FILES["image0"]["error"] > 0) {
		$error = 1;
		$error_message = $_FILES["image0"]["error"];
	} else {
		echo "Upload: " . $_FILES["image0"]["name"] . "<br />";
		echo "Type: " . $_FILES["image0"]["type"] . "<br />";
		echo "Size: " . ($_FILES["image0"]["size"] / 1024) . " Kb<br />";
		echo "Temp file: " . $_FILES["image0"]["tmp_name"] . "<br />";
	}
	}								}		



As I said, Apache isn't giving errors, the page goes fine, everything else in the form uploads and gets added to the DB.  I can see in the GET params:  image0=file.png.

I'm using Linux on the server, PHP5, Apache2. 

Any ideas? 

Thanks in advance for the help.

---

### Post by aks44 on 2008-05-08
> **mikemosher said:**
> <form id='add_file' action='index.php' method='get' enctype='multipart/form-data'>

Hint: [http://www.w3.org/TR/html401/interact/forms.html#adef-enctype](http://www.w3.org/TR/html401/interact/forms.html#adef-enctype)

;)

---

### Post by mikemosher on 2008-05-08
aks44, 

Thanks for the heads up.  I was using GET instead of POST.   

I appriciate it.

MM

---

