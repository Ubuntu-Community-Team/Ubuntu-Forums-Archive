---
title: "Uploading an image?"
date: 2012-09-16
forum: Programming Talk
---

### Post by TheodoreP on 2012-09-16
Hello,

I am having a little trouble getting a php script of mine to work properly. It's purpose is to allow registers users to post recipes with images and if no image is supplied I would like for it to jump to an alternate script to create and upload a generic "no image" or "image coming soon" image to a mysql server database. If you need any more info please let me know. I shall include the code that I have thus far.

newrecipe.inc.php
[PHP]
<?php
    
if (!isset($_SESSION['recipeuser']))
{
    echo "<h1>Sorry, your not logged in</h1>\n";
    echo "<p>Sorry, you do not have permission to post recipes. For you to post a recipe you must first register. If you are new here please use the following link to get to the registeration page. There are no subscription fees associated with this site.\n";
    echo "If you are a returning users please use the following link to login.</p>\n";
} else
{
    $userid = $_SESSION['recipeuser'];
    echo "<form enctype=\"multipart/form-data\" action=\"index.php\" method=\"post\">\n";
    echo "<table width=\"80%\" border=\"0\" cellspacing=\"5\" cellpadding=\"0\" align=\"left\">";
    echo "<tr><td colspan=\"2\" align=\"center\"><h1>Enter your Recipe</h1></td></tr>\n";
    echo "<tr><td align=\"left\"><b>Title:</b></td><td align=\"left\"><input type=\"text\" size=\"40\" name=\"title\" id=\"title\"></td></tr>\n";
    
    echo "<input type=\"hidden\" name=\"MAX_FILE_SIZE\" value=\"1024000\">\n";
   echo "<tr><td>Picture</td><td><input type=\"file\" name=\"image\"></td></tr>\n";
   echo "<tr><td colspan=\"2\"><em>Please ensure that your image is no larger than 180px x 280px.\n";
   echo " This is the size that the site will be shrinking or enlarging all images to on the main recipe page.</td></tr>\n"; 
    
    echo "<tr><td align=\"left\" colspan=\"2\"><b>Short Description</b></td></tr>\n";
    echo "<tr><td align=\"right\" colspan=\"2\"><textarea rows=\"5\" cols=\"50\" name=\"shortdesc\" id=\"shortdesc\"></textarea></td></tr>\n";
    echo "<tr><td align=\"left\" colspan=\"2\"><ingredients>Ingredients (one item per line)</ingredients></td></tr>\n";
    echo "<tr><td align=\"right\" colspan=\"2\"><textarea rows=\"10\" cols=\"50\" name=\"ingredients\" id=\"ingredients\"></textarea></td></tr>\n";
    echo "<tr><td align=\"left\" colspan=\"2\"><directions>Directions</directions></td></tr>\n";
    echo "<tr><td align=\"right\" colspan=\"2\"><textarea rows=\"10\" cols=\"50\" name=\"directions\" id=\"directions\"></textarea></td></tr>\n";
    echo "<tr><td align=\"right\" colspan=\"2\"><input type=\"submit\" value=\"Archive\" id=\"archivebtn\"></td></tr>\n";
    echo "</table>\n";

    echo "<input type=\"hidden\" name=\"poster\" value=\"$userid\"><br>\n";
    echo "<input type=\"hidden\" name=\"card\" value=\"addrecipe\">\n";
    echo "</form>\n";
}
?>
[/PHP]addrecipe.inc.php
[PHP]
<?php

  $title = $_POST['title'];
  $poster = $_POST['poster'];
  $shortdesc = $_POST['shortdesc'];
  $ingredients = htmlspecialchars($_POST['ingredients']);
  $directions = htmlspecialchars($_POST['directions']);
  
  if(get_magic_quotes_gpc())
  {
      $title = stripslashes($title);
      $shortdesc = stripslashes($shortdesc);
      $ingredients = stripslashes($ingredients);
      $directions = stripslashes($directions);
  }
  $title = mysql_real_escape_string($title);
  $shortdesc = mysql_real_escape_string($shortdesc);
  $ingredients = mysql_real_escape_string($ingredients);
  $directions = mysql_real_escape_string($directions);
  
  $thumbnail = getThumb($_FILES['image']);
  $thumbnail = mysql_real_escape_string($thumbnail);
  
  if (trim($poster == ''))
  {
     echo "<p>Sorry, each recipe must have a poster</p>\n";
  }else
  {
    $query = "INSERT INTO recipes (title, shortdesc, poster, image, ingredients, directions) " .
       " VALUES ('$title', '$shortdesc', '$poster', '$thumbnail', '$ingredients', '$directions')";

    $result = mysql_query($query) or die('Sorry, we could not post your recipe to the database at this time');

    if ($result)
       echo "<h1>Recipe posted</h1>\n";
       echo "<p>Your recipe was successfully posted to our database. To browse our current recipe selection \n";
       echo "<please follow the link below.</p><br><a href=\"index.php\">This Way Home</a>\n";
    else
       echo "<h1>Sorry</h1>\n";
       echo "<p>Sorry, there was a problem posting your recipe</p>\n";
  }
?>
[/PHP]getThumb()
[PHP]
function getThumb($Original)
{
    if(!$Original['name'])
    {
        // no image supplied, use default
        $TempName = "images/noimage.jpg";
        $TempFile = fopen($TempName,"r");
        $thumbnail = fread($TempFile,fileSize($TempName));
    } else
    {
        // get image
        $Picture = file_get_contents($Original['tmp_name']);
        
        // create image
        $SourceImage = imagecreatefromstring($Picture);
        if(!$SourceImage)
        {
            // not a valid image
            echo "Not a valid image\n";
            $TempName = "images/noimage.jpg";
            $TempFile = fopen($TempName, "r");
            $thumbnail = fread($TempFile, fileSize($TempName));
        } else
        {
            // create thumbnail
            $width = imageSX($SourceImage);
            $height = imageSY($SourceImage);
            $newThumb = imagecreatetruecolor(80,60);
            
            // resize image to 80 x 60
            $result = imagecopyresampled($newThumb, $SourceImage,
                            0,0,0,0,
                            80,60, $width, $height);
            // move image to variable
            ob_start();
            imageJPEG($newThumb);
            $thumbnail = ob_get_contents();
            ob_end_clean();
        }
    }
    return $thumbnail;
}
[/PHP]

---

### Post by spjackson on 2012-09-17
> **MasterProgram said:**
> 
I am having a little trouble getting a php script of mine to work properly. It's purpose is to allow registers users to post recipes with images and if no image is supplied I would like for it to jump to an alternate script to create and upload a generic "no image" or "image coming soon" image to a mysql server database. If you need any more info please let me know. I shall include the code that I have thus far.

I'm afraid I don't really follow what isn't working. Is it your getThumb function or something else?

---

### Post by TheodoreP on 2012-09-17
I'm not quite sure what isn't working. I know the newrecipe.inc.php file will load, after that when you click the archive button the screen goes blank. So if I would have to guess I would probably say that the addrecipe.inc.php or getThumb() function aren't working. I'm still a little new to the programming world and am still getting a feel for it. I could also be that maybe my script isn't allowing upload because of file limitations. If you could let me if and how to fix it would be greatly appreciated.

---

### Post by spjackson on 2012-09-18
> **MasterProgram said:**
> I'm not quite sure what isn't working. I know the newrecipe.inc.php file will load, after that when you click the archive button the screen goes blank. So if I would have to guess I would probably say that the addrecipe.inc.php or getThumb() function aren't working. I'm still a little new to the programming world and am still getting a feel for it. I could also be that maybe my script isn't allowing upload because of file limitations. If you could let me if and how to fix it would be greatly appreciated.
A common cause of a blank browser window when using a php is a syntax error, or failure to find an included file, or similar fault in the php script. I cannot spot this in the fragments you have posted, but these are incomplete.  For example, when you click the archive button, data is posted to index.php, but we haven't been shown index.php. We been shown code that tries to insert into the database but no code that connects to the database.

Depending on your configuration you would expect such an error to log information in the apache error log (typically /var/log/apache2/error.log), assuming that you are using apache of course. Does a row get successfully written to the database?

I do not think I can help without more information, at the very least code that I can run myself without having to invent all the missing bits.

---

### Post by TheodoreP on 2012-09-18
index.php
[PHP]
<?php
session_start();
?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
<title>Sociable Cooking</title>
<link rel="Shortcut Icon" href="images/favicon.ico" />
<link rel="stylesheet" type="text/css" href="stylesheets/layout.css" />
<link rel="stylesheet" type="text/css" href="stylesheets/textStyles.css" />
<link rel="stylesheet" type="text/css" href="stylesheets/fieldStyle.css" />
<link href='http://fonts.googleapis.com/css?family=Condiment' rel='stylesheet' type='text/css'>
</head>

<body>

<?php
require_once("myLibrary/functions.php");
connect();
?>

<div id="page">
<div id="headerBar"><?php include_once("header.inc.php"); ?>
</div>
<div id="dashboard">
<?php
if(!isset($_REQUEST['card']))
    include_once("dashboard.inc.php");
else
{
    $card = $_REQUEST['card'];
    $nextpage = $card . ".inc.php";
    include_once($nextpage);
}

?>
</div>
<div id="sideBar">
<?php
if(!isset($_SESSION['recipeuser']))
{
    include_once("register.inc.php");
}
?>
</div>
</div>

</body>
</html>
[/PHP]No a row does not get written.

If you would like all the site files let me know and I will attach a zip file with them inside. Please keep in mind that I will exclude the details of the connect() function. You I think I will go ahead and attach them now.

---

### Post by spjackson on 2012-09-19
> **MasterProgram said:**
> No a row does not get written.

If you would like all the site files let me know and I will attach a zip file with them inside. Please keep in mind that I will exclude the details of the connect() function. You I think I will go ahead and attach them now.

Ah yes, I should have been able to spot it in the first place, but I didn't.
addrecipe.inc.php
[PHP]
    if ($result)
       echo "<h1>Recipe posted</h1>\n";
       echo "<p>Your recipe was successfully posted to our database. To browse our current recipe selection \n";
       echo "<please follow the link below.</p><br><a href=\"index.php\">This Way Home</a>\n";
    else
       echo "<h1>Sorry</h1>\n";
       echo "<p>Sorry, there was a problem posting your recipe</p>\n";
[/PHP]You need braces around the branches like this.
[PHP]
    if ($result) {
       echo "<h1>Recipe posted</h1>\n";
       echo "<p>Your recipe was successfully posted to our database. To browse our current recipe selection \n";
       echo "<please follow the link below.</p><br><a href=\"index.php\">This Way Home</a>\n";
    }
    else {
       echo "<h1>Sorry</h1>\n";
       echo "<p>Sorry, there was a problem posting your recipe</p>\n";
     }
[/PHP]The error I got logged in /var/log/apache2/error.log is very helpful:
```

[Wed Sep 19 10:45:35 2012] [error] [client 192.168.1.66] PHP Parse error:  syntax error, 
unexpected T_ELSE in /home/www/SociableCooking.com/addrecipe.inc.php on line 38, 
referer: http://xxxxxxxx.xxx/SociableCooking.com/index.php?card=newrecipe

```

---

### Post by TheodoreP on 2012-09-19
Thanks, I have been trying to get this to work for quite some time and now it does. However it doesn't upload a custom no image file to the new entry if no image is supplied. If you could help me figure out an easy way to accomplish this I would greatly appreciate it.

Thanks for your help!

---

### Post by spjackson on 2012-09-19
> **MasterProgram said:**
> Thanks, I have been trying to get this to work for quite some time and now it does. However it doesn't upload a custom no image file to the new entry if no image is supplied. If you could help me figure out an easy way to accomplish this I would greatly appreciate it.

Thanks for your help!
The function getThumb loads an image from images/noimage.jpg but this doesn't exist in the tarball you uploaded. I have tested that getThumb does return an image if this file exists.

getThumb ought to have some error handling if fopen fails, and it  should also call fclose when it has finished reading the file.

---

### Post by TheodoreP on 2012-09-19
Ok I understand now. Thanks for all your help. It has been a lot more helpful here on ubuntuforums than my previously used forum.

How can I get the dashboard or main content area and side content area to be the only scrollable areas. Instead of the whole page being scrollable. The objective of this is to let the user be able to scroll through multiple recipes at once while keeping the layout intact.

---

### Post by spjackson on 2012-09-20
> **MasterProgram said:**
> Ok I understand now. Thanks for all your help. It has been a lot more helpful here on ubuntuforums than my previously used forum.

How can I get the dashboard or main content area and side content area to be the only scrollable areas. Instead of the whole page being scrollable. The objective of this is to let the user be able to scroll through multiple recipes at once while keeping the layout intact.
To make the dashboard scrollable, edit stylesheets/layout.css and in the #dashboard section add
```

overflow: auto;

```

---

### Post by TheodoreP on 2012-09-21
Now I feel really stupid I tried that and it didn't change anything, but it turns I needed to clear my browsing history. After clearing it, it works exactly how I want it too. Thanks a lot for your help.

---

### Post by TheodoreP on 2012-09-22
I now would like a little help help evaluating and debugging my site for the update recipe function. I will upload an updated tar ball. The issue I'm having is that I have a form that will display the ability to specify a file to upload but, when archive is clicked it skips over that and just updates everything else. The main files I need help debugging are probably going to be the updaterecipe.inc.php and saverecipe.inc.php.

---

### Post by spjackson on 2012-09-24
> **MasterProgram said:**
> I now would like a little help help evaluating and debugging my site for the update recipe function. I will upload an updated tar ball. The issue I'm having is that I have a form that will display the ability to specify a file to upload but, when archive is clicked it skips over that and just updates everything else. The main files I need help debugging are probably going to be the updaterecipe.inc.php and saverecipe.inc.php.
I think your problem is this.
newrecipe.inc.php:
```

      echo "<form enctype=\"multipart/form-data\" action=\"index.php\" method=\"post\">\n";

```
updaterecipe.inc.php:
```

   echo "<form action=\"index.php\" method=\"post\">\n";

```
You need to add that enctype attribute in updaterecipe.inc.php or your $_FILES array will be empty for updates.

---

### Post by TheodoreP on 2012-09-24
Thank You, that worked and now my script works perfectly.

---

### Post by spjackson on 2012-09-24
Glad to hear that!

---

### Post by TheodoreP on 2012-09-24
Currently my site is freely hosted by 000webhost.com, but for some reason when a user uploads a new recipe with a custom image or the default no image image  the mysql database is corrupting the file and my showimage.php script can't display it. Thus I am looking into new web hosts. I am open to all possibilities whether they be paid hosting or free hosting. I am just looking for a few places to start looking in.

As well if anyone knows of any way to use a desktop running Ubuntu server as a professional production server I would really like to know if it is possible. As well, does anyone know if it is possible to register a domain personally for free. If so, please explain how? Back to the Ubuntu server install info. I am wondering about if Ubuntu server is capable of being used as a production server because my parents have an old Compaq desktop in the basement that if possible I would like to use as a production server. Right now it is not being used at all. If I can use it as a production server for my site I will just do that instead of paying for hosting and save my money to upgrade the server hard drive and other equipment.

I thank you for all the information you can give me.

---

### Post by TheodoreP on 2012-09-30
Almost there! The script must need one more tweak, although it works just fine on my personal computer. However, after posting a new or updating an existing recipe the image get's truncated or corrupted and on the live site. As I said it is all good on my machine. I will upload a new tarball with this post and if you'd like to see my progress on the live site, it is hosted by A Small Orange and the address is [http://www.SociableCooking.com](http://www.SociableCooking.com).

**Please note that the site is only accessible by registered users. Please let me know what you find out here, and if it is an issue that can only be resolved by A Small Orange I let them know about it immediately.

---

### Post by TheodoreP on 2012-09-30
Nevermind, I figured it out. I just needed to adjust my mysql connection settings in the showimage.php file. The one thing I forgot to do. If you'd still like to check it out feel free to register. My site is open to all!

---

