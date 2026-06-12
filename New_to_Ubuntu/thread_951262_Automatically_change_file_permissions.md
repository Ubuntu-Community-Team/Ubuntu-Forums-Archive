---
title: "Automatically change file permissions?"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by justinram22 on 2008-10-18
Hello, i've looked on the web but can't really seem to find anything... im 13 and feel like the problems just keep coming on and on and on lol. anyway, i just set up an apache server (was that a nightmare!) and then just started learing PHP (another nightmare!) and i finally have it so people can upload files to my server, but the only problem is, i have them uploading to "/var/www/upload/" but then all the files are under root rights... im wondering if there is a way for all the files put into the "`/upload" file to change to 777 rights? I guess it isn't that big of a deal to type "sudo chmod 777 filename" but if i ever have alot of people uploading to that directory..... it would be nice to have a auto update lol... any help is greatly appreciated!

---

### Post by scragar on 2008-10-18
PHP has it's own CHMOD function, you could use that
[php]
$filename = 'blah.txt';

chmod($filename, 0777);
[/php]

---

### Post by anystupidname on 2008-10-18
disregard

---

### Post by justinram22 on 2008-10-18
Ok, sorry for asking such a stupid question, but how would i do that, so that it would name it what ever the original file name was, cause if im understanding this right the 

$filename = 'blah.txt';

would make all the files uploaded into the name "blah.txt", how would i do that so it would be the original file name? sorry again for asking such a stupid question, and thanks for all your help, and sorry if im not understanding this right

---

### Post by scragar on 2008-10-18
It depends upon your upload script, but general uploads scripts do something like:
[php]$fieldname = 'myUpload';
$newName = './uploads/someName.txt';

move_uploaded_file($_FILES[$fieldname]['tmp_name'], $newName);// You want to find the second argument, what I'm calling $newName
[/php]
If you are having trouble post your script, I'll take a look, see what I can do for you.

---

### Post by justinram22 on 2008-10-18
ok.... im still having trouble grasping this, as for im having trouble grasping PHP (tho it's alot easyer than python! lol) anyway, here is my code (this is copy and pasted from some other persons code, i found that it worked for me, but i don't understand all of it, i understand most of it tho....)

> <?php
// Upload directory: remember to give it write permission!
$uploaddir = "upload/";
// what file types do you want to disallow?
$blacklist = array(".php", ".phtml", ".php3", ".php4", ".php5", ".exe", ".js",".html", ".htm", ".inc");
 // allowed filetypes       
$allowed_filetypes = array('.jpg','.gif','.bmp','.png');
 
if (!is_dir($uploaddir)) {
    die ("Upload directory does not exists.");
}
if (!is_writable($uploaddir)) {
    die ("Upload directory is not writable.");
}
 
if ($_POST['submit']) {
 
    if (isset($_FILES['file'])) {
        if ($_FILES['file']['error'] != 0) {
            switch ($_FILES['file']['error']) {
                case 1:
                    print 'The file is too big.'; // php installation max file size error
                    exit;
                    break;
                case 2:
                    print 'The file is too big.'; // form max file size error - DEPRECATED
                    exit;
                    break;
                case 3:
                    print 'Only part of the file was uploaded.';
                    exit;
                    break;
                case 4:
                    print 'No file was uploaded.';
                    exit;
                    break;
                case 6:
                    print "Missing a temporary folder.";
                    exit;
                    break;
                case 7:
                    print "Failed to write file to disk";
                    exit;
                    break;
                case 8:
                    print "File upload stopped by extension";
                    exit;
                    break;
            }
        } else {
            foreach ($blacklist as $item) {
                if (preg_match("/$item\$/i", $_FILES['file']['name'])) {
                    echo "Invalid filetype !";
                    unset($_FILES['file']['tmp_name']);
                    exit;
                }
            }
            // Get the extension from the filename.
            $ext = substr($_FILES['file']['name'], strpos($_FILES['file']['name'],'.'), strlen($_FILES['file']['name'])-1);
			// Check if the filetype is allowed, if not DIE and inform the user.
			if(!in_array($ext,$allowed_filetypes)){
				die('The file you attempted to upload is not allowed.');
			}
			if (!file_exists($uploaddir . $_FILES["file"]["name"])) {
				// Proceed with file upload
				if (is_uploaded_file($_FILES['file']['tmp_name'])) {
					//File was uploaded to the temp dir, continue upload process
					if (move_uploaded_file($_FILES['file']['tmp_name'], $uploaddir . $_FILES['file']['name'])) {
						// uploaded file was moved and renamed succesfuly. Display a message.
						echo "Upload successful!";
					} else {
						echo "Error while uploading the file, Please contact the webmaster.";
						unset($_FILES['file']['tmp_name']);
					}
				} else {
					//File was NOT uploaded to the temp dir
					switch ($_FILES['file']['error']) {
						case 1:
							print 'The file is too big.'; // php installation max file size error
							break;
						case 2:
							print 'The file is too big.'; // form max file size error
							break;
						case 3:
							print 'Only part of the file was uploaded';
							break;
						case 4:
							print 'No file was uploaded';
							break;
						case 6:
							print "Missing a temporary folder.";
							break;
						case 7:
							print "Failed to write file to disk";
							break;
						case 8:
							print "File upload stopped by extension";
							break;			
					}			
				}
			} else { // There's a file with the same name
				echo "Filename already exists, Please rename the file and retry.";
				unset($_FILES['file']['tmp_name']);
			}
        }
    } else { // user did not select a file to upload
        echo "Please select a file to upload.";       
    }
} else { // upload button was not pressed
    header("Location: form.html");
}
?>

---

### Post by scragar on 2008-10-18
Please replace your [noparse]>  tags for the [php] tags, same for the closing tag, replace  with [/php][/noparse], thanks.

And after this line:

[php]if (move_uploaded_file($_FILES['file']['tmp_name'], $uploaddir . $_FILES['file']['name'])) {[/php]
just add in 1 more line:
[php]
chmod($_FILES['file']['name'], 0777);
[/php]

---

### Post by justinram22 on 2008-10-18
Ok, im sorry for being so needy, but i added the line [php] chmod($_FILES['file']['name'], 0777); [/php] and this is the output i get when i tried to upload something to my server
>  

Warning: chmod() [function.chmod]: No such file or directory in /var/www/upload.php on line 71
Upload successful!



Thanks again

---

### Post by scragar on 2008-10-18
Bah, stupid unsetting rules.

[php].....

if (is_uploaded_file($_FILES['file']['tmp_name'])) {
//File was uploaded to the temp dir, continue upload process
		$tmpName = $_FILES["file"]["name"];
if (move_uploaded_file($_FILES['file']['tmp_name'], $uploaddir . $tmpName)) {
		chmod($tmpName, 0777);
// uploaded file was moved and renamed succesfuly. Display a message.
echo "Upload successful!";

....[/php]

---

### Post by justinram22 on 2008-10-18
..... lol sorry for being such a hassle... but still no go, says exact same thing when typed this in

[php] if (is_uploaded_file($_FILES['file']['tmp_name'])) {
//File was uploaded to the temp dir, continue upload process
        $tmpName = $_FILES["file"]["name"];
if (move_uploaded_file($_FILES['file']['tmp_name'], $uploaddir . $tmpName)) {
        chmod($tmpName, 0777);
// uploaded file was moved and renamed succesfuly. Display a message.
echo "Upload successful!"; [/php]

i even experimented a little, but that didn't seem to help.. with

[php] if (is_uploaded_file($_FILES['file']['tmp_name'])) {
//File was uploaded to the temp dir, continue upload process
        $tmpName = $_FILES['file']['name'];
if (move_uploaded_file($_FILES['file']['tmp_name'], $uploaddir . $tmpName)) {
        chmod($tmpName, 0777);
// uploaded file was moved and renamed succesfuly. Display a message.
echo "Upload successful!"; [/php]
Thanks a lot!

---

### Post by scragar on 2008-10-18
oh, poopy, always the obvious things I miss lol.

[php]
chmod(          $uploaddir.             $tmpName, 0777); 
[/php]
see the bit between the 2 big gaps, put that in. I can't belive I missed it before

---

### Post by justinram22 on 2008-10-18
Thank you so much!! i can't thank you enough!!!! Thank you for all your help!

---

