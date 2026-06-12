---
title: "PHP Upload Script Help."
date: 2010-03-08
forum: Programming Talk
---

### Post by Crafty Kisses on 2010-03-08
Hello guys, me and my friend have this project going that needs a uploader, so people can upload video files and what not to our website. Here is the current PHP script we have:

```
<?php
	if (isset($_POST["PHPSESSID"])) {
		session_id($_POST["PHPSESSID"]);
	} else if (isset($_GET["PHPSESSID"])) {
		session_id($_GET["PHPSESSID"]);
	}

	session_start();


	$POST_MAX_SIZE = ini_get('post_max_size');
	$unit = strtoupper(substr($POST_MAX_SIZE, -1));
	$multiplier = ($unit == 'M' ? 1048576 : ($unit == 'K' ? 1024 : ($unit == 'G' ? 1073741824 : 1)));

	if ((int)$_SERVER['CONTENT_LENGTH'] > $multiplier*(int)$POST_MAX_SIZE && $POST_MAX_SIZE) {
		header("HTTP/1.1 500 Internal Server Error"); 
		echo "POST exceeded maximum allowed size.";
		exit(0);
	}


	$save_path = dirname(__FILENAME__) . "/home/rthteddy/public_html/upload";				
	$upload_name = "Filedata";
	$max_file_size_in_bytes = 2147483647;				
	$extension_whitelist = array("jpg", "gif", "png");	
	$valid_chars_regex = '.A-Z0-9_ !@#$%^&()+={}\[\]\',~`-';				file name (in a Regular Expression format)
	

	$MAX_FILENAME_LENGTH = 260;
	$file_name = "";
	$file_extension = "";
	$uploadErrors = array(
        0=>"There is no error, the file uploaded successfully",
        1=>"The uploaded file exceeds the upload_max_filesize directive in php.ini",
        2=>"The uploaded file exceeds the MAX_FILE_SIZE directive that was specified in the HTML form",
        3=>"The uploaded file was only partially uploaded",
        4=>"No file was uploaded",
        6=>"Missing a temporary folder"
	);



	if (!isset($_FILES[$upload_name])) {
		HandleError("No upload found in \$_FILES for " . $upload_name);
		exit(0);
	} else if (isset($_FILES[$upload_name]["error"]) && $_FILES[$upload_name]["error"] != 0) {
		HandleError($uploadErrors[$_FILES[$upload_name]["error"]]);
		exit(0);
	} else if (!isset($_FILES[$upload_name]["tmp_name"]) || !@is_uploaded_file($_FILES[$upload_name]["tmp_name"])) {
		HandleError("Upload failed is_uploaded_file test.");
		exit(0);
	} else if (!isset($_FILES[$upload_name]['name'])) {
		HandleError("File has no name.");
		exit(0);
	}
	

	$file_size = @filesize($_FILES[$upload_name]["tmp_name"]);
	if (!$file_size || $file_size > $max_file_size_in_bytes) {
		HandleError("File exceeds the maximum allowed size");
		exit(0);
	}
	
	if ($file_size <= 0) {
		HandleError("File size outside allowed lower bound");
		exit(0);
	}



	$file_name = preg_replace('/[^'.$valid_chars_regex.']|\.+$/i', "", basename($_FILES[$upload_name]['name']));
	if (strlen($file_name) == 0 || strlen($file_name) > $MAX_FILENAME_LENGTH) {
		HandleError("Invalid file name");
		exit(0);
	}



	if (file_exists($save_path . $file_name)) {
		HandleError("File with this name already exists");
		exit(0);
	}

	$path_info = pathinfo($_FILES[$upload_name]['name']);
	$file_extension = $path_info["extension"];
	$is_valid_extension = false;
	foreach ($extension_whitelist as $extension) {
		if (strcasecmp($file_extension, $extension) == 0) {
			$is_valid_extension = true;
			break;
		}
	}
	if (!$is_valid_extension) {
		HandleError("Invalid file extension");
		exit(0);
	}


	*/
	if (!@move_uploaded_file($_FILES[$upload_name]["tmp_name"], $save_path.$file_name)) {
		HandleError("File could not be saved.");
		exit(0);
	}

	exit(0);


function HandleError($message) {
	echo $message;
}
?>
```
The issue is, everytime we try to upload a file it says:
```
File could not be saved
```
That's no matter how big and what type of file it is, we have only tried uploading images, as that's what the code only allows as of now. We have the "upload" directory, and that's at 777 permissions, so I'm not quite sure what to do next. Any help would be GREATLY appreciated.

---

### Post by DaithiF on 2010-03-08
Hi,
are the parent directories of the upload dir also accessible by the webserver?  i.e. its not necessarily enough for just the last directory to be writeable, if the webserver user can't actually get that far due to permission restrictions higher up the path.

---

### Post by Crafty Kisses on 2010-03-08
I'm pretty sure the path is the highest. I mean, I'm kind of new to PHP. So I'm not sure how exactly how this stuff works, but I will tell you our exact setup, it's like most peoples. I have a root directory, and then a **public_html** directory. I upload the upload script to the public_html directory, that's where the "upload" directory is, which has 777 permissions. So in the PHP code, I did:

```
$save_path = dirname(__FILENAME__) . "/home/rthteddy/public_html/upload";
```

So in some essence, when people upload files, it should go to that directory, am I right? I think I am, but I'm really new to PHP and what not, so please correct me if I'm wrong. Ok so now that we have got that out of the way, we are using **name.com** as our hosting service, now do you think it could possibly be an issue with them? I do see PHP configuration options and what not, but I'm just not quite sure that will solve this problem, as there is nothing that points to upload options in that section.

I'm sorry, I'm just kind of new, so any help is really appreciated. So are you suggesting maybe I upload the "upload" directory to the root directory of our website? Thanks, I just need a bit of clarification. Thank you so much.

---

### Post by DaithiF on 2010-03-08
Hi,
i'm not a php developer, but the save path looks weird, why is it not just:
$save_path = "/home/rthteddy/public_html/upload";
The way its written above would result in a location of:
"/home/rthteddy/public_html/home/rhteddy/public_html/upload", which (presumably) doesn't exist

---

### Post by Hellkeepa on 2010-03-08
HELLo!

You're entirely correct, **DaithiF**.
It could even be just "upload/", as PHP works relative from the path of the landing file. The landing file in this case would presumably be "domain.com/upload.php", which is stored in the "public_html" folder. So if the "$save_path" variable is set to just "upload/" it would expand to "[COLOR="RoyalBlue"]/home/rhteddy/public_html/[/COLOR]upload/" when used. Where the blue bit is taken from the path of the "upload.php" file's path.

I would also like to point out that you have two syntax errors in the script, regarding comments. One on line 24 and one on line 87.
Lines 2-6 should be unnecessary, as PHP handles the SessionID handling by itself. At least if it's set up correctly, and the code is sound.
Checking the actual MIME-type of the file is something I'd do in addition to the checks that you're already doing, but other than that it seems like a reasonably secure script. Haven't given it a rigorous test though, but I couldn't spot any immediate flaws.

Happy codin'!

---

### Post by Crafty Kisses on 2010-03-10
So I ended up getting my PHP script to work, but I can't seem to get .flv files to upload, any ideas? Here is my script:
```
<?php
   // Configuration - Your Options
      $allowed_filetypes = array('.jpg','.gif','.bmp','.png','video/x-flv','flv-application/octet-stream','application/octet-stream','.flv','images','flash'); // These will be the types of file that will pass the validation.
      $max_filesize = 52428800 ; // Maximum filesize in BYTES (currently 0.5MB).
      $upload_path = './upload/'; // The place the files will be uploaded to (currently a 'files' directory).
 
   $filename = $_FILES['userfile']['name']; // Get the name of the file (including file extension).
   $ext = substr($filename, strpos($filename,'.'), strlen($filename)-1); // Get the extension from the filename.
 
   // Check if the filetype is allowed, if not DIE and inform the user.
   if(!in_array($ext,$allowed_filetypes))
      die('The file you attempted to upload is not allowed.');
 
   // Now check the filesize, if it is too large then DIE and inform the user.
   if(filesize($_FILES['userfile']['tmp_name']) > $max_filesize)
      die('The file you attempted to upload is too large.');
 
   // Check if we can upload to the specified path, if not DIE and inform the user.
   if(!is_writable($upload_path))
      die('You cannot upload to the specified directory, please CHMOD it to 777.');
 
   // Upload the file to your specified path.
   if(move_uploaded_file($_FILES['userfile']['tmp_name'],$upload_path . $filename))
         echo 'Your file upload was successful, view the file <a href="' . $upload_path . $filename . '" title="Your File">here</a>'; // It worked.
      else
         echo 'There was an error during the file upload.  Please try again.'; // It failed :(.
 
?>
```

---

### Post by DaithiF on 2010-03-10
you don't say where it fails.  is it due to the filetype check -- die('The file you attempted to upload is not allowed.');  or elsewhere?

---

### Post by Crafty Kisses on 2010-03-10
> **DaithiF said:**
> you don't say where it fails.  is it due to the filetype check -- die('The file you attempted to upload is not allowed.');  or elsewhere?

That's exactly where it fails. I'm thinking it might have something to do with that 2MB cap PHP has, but I checked my max_upload_size, and it said 64MB.

---

### Post by DaithiF on 2010-03-10
> Originally Posted by **DaithiF** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=8943994#post8943994") 				
 				*you don't say where it fails. is it due to the filetype check -- die('The file you attempted to upload is not allowed.'); or elsewhere?*
 			 		 	 	 That's exactly where it fails. I'm thinking it might have something to do with that 2MB cap PHP has, but I checked my max_upload_size, and it said 64MB.
if it fails at the point I asked about then its because the file extension isn't one of the types you specify in the $allowed_filetypes array.  What is the name of the file, in particular is its extension .flv (and not, for example .FLV, .Flv, etc)?

---

### Post by Crafty Kisses on 2010-03-10
Yeah, the file is called "Football.flv".

---

### Post by DaithiF on 2010-03-10
I don't see why it would fail at that point with a file of that extension.

Just regarding your comment about max upload size, you are aware I assume that your script is enforcing a max upload size of 0.5MB?  

You say it is failing with the message: 'The file you attempted to upload is not allowed.', rather than 'The file you attempted to upload is too large'.  Is that correct?

---

### Post by Hellkeepa on 2010-03-10
HELLo!

I notice that you're mixing file extensions, MIME types and some random strings in the same test. Which does not make any sense at all. If you're going to test file extensions, then you need to clean up that array so that it only contains extensions. For testing MIME types you need a completely different test, using it's own source array for allowed MIME types.

To split the filename into its base components, you should also look into using "[pathinfo ()](http://no2.php.net/manual/en/function.pathinfo.php), like this:
[php]list ($filename, $ext) = pathinfo ($_FILES['userfile']['name'], PATHINFO_EXTENSION | PATHINFO_FILENAME);[/php]
Also, I recommend using "strtolower ()" when checkign the file extension, just to make sure that everything is in lower case.

That said, I do recommend that you go back to the original script. This one is far too insecure. Just remove the "\." at the end of the filename RegExp check in it, as taht'll allow just about any character.

Happy codin'!

---

