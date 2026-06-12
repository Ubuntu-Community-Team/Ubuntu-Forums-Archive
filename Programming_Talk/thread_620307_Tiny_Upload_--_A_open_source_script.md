---
title: "Tiny Upload -- A open source script"
date: 2007-11-22
forum: Programming Talk
---

### Post by 7Priest7 on 2007-11-22
No Code For Ubuntu Forums

---

### Post by Kadrus on 2007-11-22
> **7Priest7 said:**
> [php]
<?php
// Tiny Upload
// By: Alexander Leonn Santiago
// Open Source

$dir = "files/"; // Place to store files
$url = "http://alsfh.gigacities.net/"; // Your sites URL... Used for links later
$pw = ""; // A password to prevent unauthorized access
$yn = ""; // Your name
if($_FILES["file"]["tmp_name"] && $_POST['pass'] == $pw) // If an authorized person tries to post file
{
   $ext = pathinfo($_FILES['file']['name'],PATHINFO_EXTENSION); // Find extension of files
   $ext = strtolower($ext); // Make it lower case
   if($ext != "php" && !@is_file("{$dir}{$_FILES['file']['name']}")) // Make sure it is not a PHP file and does not already exist
   {
      move_uploaded_file($_FILES["file"]["tmp_name"], "{$dir}" . $_FILES["file"]["name"]); // Upload it
   }
}
if($_POST['pass'] == $pw && !is_file("{$dir}ban/{$_SERVER['REMOTE_ADDR']}")) // Starts HTML for authorized person
{
   echo("<!DOCTYPE HTML PUBLIC '-//W3C//DTD HTML 4.0 Transitional//EN' 'http://www.w3.org/TR/REC-html40/loose.dtd'>\n<html>\n<head>\n<meta http-equiv='Content-Type' content='text/html; charset=US-ASCII'>\n<title>{$yn}s File Host</title>\n</head>\n<body>\n"); // HTML Head element and Body element opening tag
   echo("<form action='/' method='post' enctype='multipart/form-data'>\n"); // Beginning of Upload form
   echo("<input name='file' type='file'>\n<input type='hidden' value='{$_POST['pass']}' name='pass'>\n<input type='submit' value='Dump File'>\n"); // Input file/hidden password/submit button
   echo("</form>\n"); // End the form
   if($dirls = @opendir("{$dir}")){ // If we open the directory
      while($file = @readdir($dirls)){ // While there are files
         if($file != "." && $file != ".." && $file != "ban") // They are not dot notation or ban subdir
            echo("<a href='{$url}{$dir}{$file}'>{$file}</a><br>\n");} // Echo a link to the file
      closedir($dirls); // Close the directory
   }
   echo("</body>\n</html>"); // End the body and html
}
else if($_POST['pass']) // They entered an incorrect Password
   file_put_contents("{$dir}ban/{$_SERVER['REMOTE_ADDR']}",""); // Ban Them 
else // Evrebody sees this before they try to enter
{
   echo("<!DOCTYPE HTML PUBLIC '-//W3C//DTD HTML 4.0 Transitional//EN' 'http://www.w3.org/TR/REC-html40/loose.dtd'>\n<html>\n<head>\n<meta http-equiv='Content-Type' content='text/html; charset=US-ASCII'>\n<title>{$yn}s File Host</title>\n</head>\n<body>\n"); // HTML head element and Body element opening tag
   echo("<form action='/' method='post'><input name='pass' type='text'><input value='Enter' type='submit'></form>"); // Form to enter Password
   echo("</body>\n</html>"); // End body/html
}
?>
[/php]
This is a minamalist script
This script is for people who are tired of sites like megaupload.com or photobucket.com

Enjoy :)

Alex

Related URLs:
[http://alsfh.gigacities.net/](http://alsfh.gigacities.net/) -- Working example
[http://validator.w3.org/check?uri=http%3A%2F%2Falsfh.gigacities.net%2F&charset=%28detect+automatically%29&doctype=Inline&group=0](http://validator.w3.org/check?uri=http%3A%2F%2Falsfh.gigacities.net%2F&charset=%28detect+automatically%29&doctype=Inline&group=0) -- Proof of valid HTML

Suggested Hosts:
[http://gigacities.net/](http://gigacities.net/) -- Alot of space and bandwidth (is a little slow sometimes)
[http://freewebhosting360.com](http://freewebhosting360.com) -- Less space but faster... I think this one has filesize limits :(
[http://free-webhosts.com](http://free-webhosts.com) -- To find a host that meets your needs

Pretty sweet.. :)

---

### Post by 7Priest7 on 2007-11-23
I added an additional authorized check to the upload segement "!is_file("{$dir}ban/{$_SERVER['REMOTE_ADDR']}")"
Now some1 cannot create a custom script/form and hack based off random password generator

Enjoy :)

Alex

---

### Post by mellowd on 2007-11-23
Where exactly does it upload the file to? I've put the php file on the root of my domain and cant seem to find the file i uploaded

---

### Post by 7Priest7 on 2007-11-23
83.150.85.2
^ First hack attempt...
To the owner:
It does prove my script can/will ban and It functions...

Nice Try :)

Alex

---

### Post by 7Priest7 on 2007-11-23
> **mellowd said:**
> Where exactly does it upload the file to? I've put the php file on the root of my domain and cant seem to find the file i uploaded

I should have explained that on my first post...
On the root...
This script is Index.php...
You will need a directory on the root name "files" or whatever you put as dir variable
That directory needs file permissions 777
All read write and execute...
Inside the folder you need a ban folder...
Which also needs file permission 777

Hope I helped :)

Alex

EDIT: I just uploaded this a minute ago to prove it does work [http://alsfh.gigacities.net/files/Alexander.jpg](http://alsfh.gigacities.net/files/Alexander.jpg)
:)
EDIT: Apparently Gigacities sets some bad default permissions that prevent you from viewing the above jpg... That is host specific though...
You should not have that problem
Alex

---

### Post by mellowd on 2007-11-23
let me test

---

### Post by mellowd on 2007-11-23
Not sure if I'm doing it wrong. Now when I open it I'm assuming its asking me for my password. I enter that and click enter but then it just takes me to the root of my domain

---

### Post by LaRoza on 2007-11-23
> **7Priest7 said:**
> 83.150.85.2
^ First hack attempt...
To the owner:
It does prove my script can/will ban and It functions...

Here is the "attacking" site: [http://83.150.85.2/](http://83.150.85.2/)

---

### Post by 7Priest7 on 2007-11-23
> **mellowd said:**
> Not sure if I'm doing it wrong. Now when I open it I'm assuming its asking me for my password. I enter that and click enter but then it just takes me to the root of my domain

Can You message me the mods you made to the script and the url in which it is located?

---

### Post by mellowd on 2007-11-23
done

---

### Post by 7Priest7 on 2007-11-23
The problem mellowed had was in the form action...
He wanted it to be called upload.php...
So for future refrence to anyone who uses it, and decides not to name it index.php, You need to change the form action

:)

Alex

---

### Post by 7Priest7 on 2007-11-23
I added the chmod function...
I was having some problems with my default permissions...
I used the following to fix it
[php]
<?php
$dir = "files/"; // Place to store files
   if($dirls = @opendir("{$dir}")){ // If we open the directory
      while($file = @readdir($dirls)){ // While there are files
         if($file != "." && $file != ".." && $file != "ban") // They are not dot notation or ban subdir
            chmod("{$dir}{$file}", 0755);}
      closedir($dirls); // Close the directory
      
   }
?>
[/php]

Enjoy :)

Alex

---

### Post by 7Priest7 on 2007-11-24
I added the ability to delete files and I added a site for you guys to test my script...

Right now you can only delete one file at a time...
I want it to be able to delete more...
I'll probably add that later...

Enjoy :)

Alex

---

### Post by mellowd on 2007-11-24
do you have the sites url?

---

### Post by 7Priest7 on 2007-11-24
> **mellowd said:**
> do you have the sites url?

I put it on Post #1

Hope I Helped :)

Alex

---

### Post by 7Priest7 on 2007-11-24
Please Note:
I am not the sellout that put ads on the quotaless site...
It is the price I pay for having unlimited space/bandwidth

Please forgive the sellouts :)

Alex

---

