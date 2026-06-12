---
title: "Cant figure it out for the life of me.. PHP syntax"
date: 2010-03-13
forum: Programming Talk
---

### Post by StaticIp on 2010-03-13
Im trying to use this script to allow clients to upload files to their user directory. The code should grab their username from the cookie set when they login. I know the cookie is set properly and I can read from it with other php code. 

[PHP]<?php

	$uploaddir = '../clients/'$HTTP_COOKIE_VARS['cookname']'/uploads/';

	$file = $uploaddir . basename($_FILES['uploadfile']['name']);

	$size=$_FILES['uploadfile']['size'];

if($size>1048576)

{

	echo "error file size > 1 MB";

	unlink($_FILES['uploadfile']['tmp_name']);

	exit;

}

if (move_uploaded_file($_FILES['uploadfile']['tmp_name'], $file)) {

  echo "success";

} else {

	echo "error ".$_FILES['uploadfile']['error']." --- ".$_FILES['uploadfile']['tmp_name']." %%% ".$file."($size)";

}

?>[/PHP]

Line 2 keeps giving me 

```
Parse error:  syntax error, unexpected T_VARIABLE in /var/www/php/upload-file.php on line 2
```

I googled all I could to try and figure this out, if anyone has any suggestions please let me know.
         Thanks.

Page calling php:
[HTML]<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">

<html xmlns="http://www.w3.org/1999/xhtml">

<head>

<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />

<title></title>

<script type="text/javascript" src="js/jquery-1.3.2.js"></script>

<script type="text/javascript" src="js/swfupload.js"></script>

<script type="text/javascript" src="js/jquery.swfupload.js"></script>

<script type="text/javascript">



$(function(){

	$('#swfupload-control').swfupload({

		upload_url: "php/upload-file.php",

		file_post_name: 'uploadfile',

		file_size_limit : "10000000",

		file_types : "*.jpg;*.png;*.gif;*.rar;*.mp3;*.wma",

		file_types_description : "All files",

		file_upload_limit : 900,

		flash_url : "flash/swfupload.swf",

		button_image_url : 'images/wdp_buttons_upload_114x29.png',

		button_width : 114,

		button_height : 29,

		button_placeholder : $('#button')[0],

		debug: true

	})

		.bind('fileQueued', function(event, file){

			var listitem='<li id="'+file.id+'" >'+

				'File: <em>'+file.name+'</em> ('+Math.round(file.size/1024)+' KB) <span class="progressvalue" ></span>'+

				'<div class="progressbar" ><div class="progress" ></div></div>'+

				'<p class="status" >Pending</p>'+

				'<span class="cancel" >&nbsp;</span>'+

				'</li>';

			$('#log').append(listitem);

			$('li#'+file.id+' .cancel').bind('click', function(){

				var swfu = $.swfupload.getInstance('#swfupload-control');

				swfu.cancelUpload(file.id);

				$('li#'+file.id).slideUp('fast');

			});

			// start the upload since it's queued

			$(this).swfupload('startUpload');

		})

		.bind('fileQueueError', function(event, file, errorCode, message){

			alert('Size of the file '+file.name+' is greater than limit');

		})

		.bind('fileDialogComplete', function(event, numFilesSelected, numFilesQueued){

			$('#queuestatus').text('Files Selected: '+numFilesSelected+' / Queued Files: '+numFilesQueued);

		})

		.bind('uploadStart', function(event, file){

			$('#log li#'+file.id).find('p.status').text('Uploading...');

			$('#log li#'+file.id).find('span.progressvalue').text('0%');

			$('#log li#'+file.id).find('span.cancel').hide();

		})

		.bind('uploadProgress', function(event, file, bytesLoaded){

			//Show Progress

			var percentage=Math.round((bytesLoaded/file.size)*100);

			$('#log li#'+file.id).find('div.progress').css('width', percentage+'%');

			$('#log li#'+file.id).find('span.progressvalue').text(percentage+'%');

		})

		.bind('uploadSuccess', function(event, file, serverData){

			var item=$('#log li#'+file.id);

			item.find('div.progress').css('width', '100%');

			item.find('span.progressvalue').text('100%');

			var pathtofile='<a href="uploads/'+file.name+'" target="_blank" >view &raquo;</a>';

			item.addClass('success').find('p.status').html('Done!!! | '+pathtofile);

		})

		.bind('uploadComplete', function(event, file){

			// upload has completed, try the next one in the queue

			$(this).swfupload('startUpload');

		})

	

});	



</script>

<style type="text/css" >

#swfupload-control p{ margin:10px 5px; font-size:0.9em; }

#log{ margin:0; padding:0; width:500px;}

#log li{ list-style-position:inside; margin:2px; border:1px solid #ccc; padding:10px; font-size:12px; 

	font-family:Arial, Helvetica, sans-serif; color:#333; background:#fff; position:relative;}

#log li .progressbar{ border:1px solid #333; height:5px; background:#fff; }

#log li .progress{ background:#999; width:0%; height:5px; }

#log li p{ margin:0; line-height:18px; }

#log li.success{ border:1px solid #339933; background:#ccf9b9; }

#log li span.cancel{ position:absolute; top:5px; right:5px; width:20px; height:20px; 

	background:url('images/cancel.png') no-repeat; cursor:pointer; }

</style>

</head>

<body>

	<h3>&raquo; Multiple File Upload With Progress Bar</h3>

	

<div id="swfupload-control">

	<input type="button" id="button" />

	<p id="queuestatus" ></p>

	<ol id="log"></ol>

</div>

</body>

</html>[/HTML]

---

### Post by korvirlol on 2010-03-14
try changing it to:
[PHP]
$uploaddir = '../clients/' . $HTTP_COOKIE_VARS['cookname'] . '/uploads/';[/PHP]


edit: those are dots

---

### Post by StaticIp on 2010-03-14
No more syntax errors, but now its
[HTML]SWF DEBUG: <b>Warning</b>:  move_uploaded_file() [<a href='function.move-uploaded-file'>function.move-uploaded-file</a>]: Unable to move '/tmp/phpkGECke' to '../clients//uploads/106773-gl.org_jwm_ubuntuwall2.jpg' in <b>/var/www/php/upload-file.php</b> on line <b>11</b><br />
SWF DEBUG: error 0 --- /tmp/phpkGECke %%% ../clients//uploads/106773-gl.org_jwm_ubuntuwall2.jpg(726732)[/HTML]

Its just not injecting the variable from the cookie.

---

### Post by soltanis on 2010-03-14
Yes, either you should be concatenating those strings (the . operator) or you should use

```

$interpolation = "fun!";
$var = "string $interpolation";
# $var = "string fun!"

```

---

### Post by Compyx on 2010-03-14
The use of $HTTP_COOKIE_VARS is deprecated since PHP 4.1.0, try the super-global $_COOKIE instead.

Try printing $HTTP_COOKIE_VARS and $_COOKIE with print_r() to see if anything is there at all and turn up your warning levels:
[php]
error_reporting(E_ALL|E_STRICT);
[/php]

---

### Post by Hellkeepa on 2010-03-14
HELLo!

There are a few things here that should be improved. I suspect that you're fairly new to PHP, and that most of this code was copied from tutorials and such? If this is indeed the case, then I recommend that you read through the [PHP manual](http://www.php.net/manual/en/index.php). At least the chapters "Getting started", "Language reference" and "Security".
Will help you get a much better understanding of PHP, and avoid most simple issues. ;-)

Now, to your code. Just making a quick list of the things to improve here:
[list][*]"$HTTP_COOKIE_VARS" is old, and might be disabled on your server. Use "$_COOKIE" instead.
[*]No validation of the cookies content, meaning any user could write whatever he likes into it. This opens for abuse of the upload script, to upload stuff to wherever the attacker wants. Including the possibility to abuse NULL bytes to terminate the filename/path early, and then overwrite your own PHP files.
[*]Storing the username in cookies, which are stored on the browser in clear text, and sent as clear text over the network. Allows an attacker to use whatever username he likes, even if he's not logged in. (It's as simple as creating a text file on your own computer to fool this.)
Use sessions to store such data instead.
[*]Although you're using "basename ()" to get ensure you don't get any path component in the filename, you're still not validating it to make sure it is a legal filename. Could cause various issues with your system, up to FS corruption.
[*]Not checking if the size is > 0. Should speak for itself. :-P
[*]Use "is_uploaded_file ()" before trying to move it, to ensure that this is indeed an uploaded file and not an attack to read a system file.
[*]"$_FILES['uploadfile']['error']" and "$_FILES['uploadfile']['tmp_name']" echoed out to the browser without escaping the content, something which opens up for XSS and similar attacks. Use "htmlspecialchars ()" to make sure the content is secure for printing out to HTML code.
[*]General lack of testing the files for correct content/type.
Even if you have client-side checks for this in the SWF and JS, it is easy to upload to your file without having to go through these. Meaning an can send whatever data to your upload form, and have it accepted without problems.[/list]
When it comes to security on the web, these are the two most important rules:
[list=1][*]Never trust data from the client/browser.
[*]Do not underestimate the dark side.[/list]
I suggest in fixing up in the issues mentioned above. When you've rewritten your script to use sessions instead of cookies, then we can have a better look at the script if it shows the same issues then. ;-)

Happy codin'!

---

