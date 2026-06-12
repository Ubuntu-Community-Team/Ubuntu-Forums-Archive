---
title: "php help"
date: 2005-12-23
forum: Programming Talk
---

### Post by grim918 on 2005-12-23
im trying to set up a php script that will allow users to upload files on to my server. everytime that i try to upload a file from another computer on to the server i get an error saying that i dont have permission to write to the specified directory. can anyone help me out on how i can change the php script to allow user uploads.
here is my simple php upload script:

<?php
$file_dir = "/directory path//";
foreach($_FILES as $file_name => $file_array) {
	echo "path: ".$file_array['tmp_name']."<br />\n";
	echo "name: ".$file_array['name']."<br />\n";
	echo "type: ".$file_array['type']."<br />\n";
	echo "size: ".$file_array['size']."<br />\n";

	if(is_uploaded_file($file_array['tmp_name'])){
		move_uploaded_file($file_array['tmp_name'],
		  "$file_dir/$file_array[name]") or die("Couldn't copy");
		echo "file was moved!<br /><br />";
	}
}
?>

thanks to anyone that can help me out.

---

### Post by sapo on 2005-12-23
You need to chmod 777 the dir before trying to upload files into it, but also check if safe mode is enabled on your server

---

### Post by grim918 on 2005-12-23
im new to linux. how do i chmod 777 the dir. and how do i check if my server is in safe mode. id appreciate any help that you can give me.

---

### Post by nemik on 2005-12-23
well make a info.php and put this in it:

```

<?
phpinfo();
?>

```

then hit it with a browser and search for safe_mode, see if it is on.

as for the folder, which FTP client do you use? in most you can right click on the directory and chmod or change permissions. there change it to 777 and it will be fine.

---

### Post by grim918 on 2005-12-23
ok i chmod 777 the dir. my file uploader is now working thanks to you guyz.
but i checked and safe_mode is not enabled on my server. it is off. should it be enabled and if it should where can i change it. thank you

---

### Post by nemik on 2005-12-23
no, it is much better and you have more control with it off. but with all such control, come responsibilities. just don't do anything too stupid, you'll be fine and your host won't get mad.

---

### Post by grim918 on 2005-12-23
ok thank you for the help. linux is a bit confusing. but i luv it.

---

