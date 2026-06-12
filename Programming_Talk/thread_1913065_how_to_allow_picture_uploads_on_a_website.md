---
title: "how to allow picture uploads on a website?"
date: 2012-01-21
forum: Programming Talk
---

### Post by anon0 on 2012-01-21
How would you add the functionality of allowing data uploads in the form of pictures? What kind of structure should be used by the server to store the pics? Assume the server is LAMP based. Thanks!

---

### Post by |{urse on 2012-01-21
You'll need to be a little more specific. When you say upload pictures do you mean uploaded via ftp by the site owners, or are you wanting someone to show you the necessary code to write a gallery/submission page with or without a database full of registered users? 

What is your current programming skillset?

Is this for like.. a gallery you are hoping to sell to a customer so they can self-maintain it? 

ANYWAYS,

Youll need to write the code for the submission form, 

[http://www.w3schools.com/html/html_forms.asp](http://www.w3schools.com/html/html_forms.asp)

You'll need to install and learn both PHP and mysql on your webserver.

[http://mrarrowhead.com/index.php?page=store_images_mysql_php.php](http://mrarrowhead.com/index.php?page=store_images_mysql_php.php)

You'll need to fetch and display those images

[http://mrarrowhead.com/index.php?page=retreive_images_mysql_php.php](http://mrarrowhead.com/index.php?page=retreive_images_mysql_php.php)

You'll need to display those images in an organized and attractive manner so you'll want to learn how to use jquery.

[http://www.1stwebdesigner.com/css/fresh-jquery-image-gallery-display-solutions/](http://www.1stwebdesigner.com/css/fresh-jquery-image-gallery-display-solutions/)

---

### Post by anon0 on 2012-01-22
> **|{urse said:**
> are you wanting someone to show you the necessary code to write a gallery/submission page with or without a database full of registered users? 

What is your current programming skillset?

Is this for like.. a gallery you are hoping to sell to a customer so they can self-maintain it? 

Yeah it'd be for registered users on a website to upload pictures for their profiles. I want the user to be able to click a button on the webpage to upload a picture to the server. So is this  done by inserting the file into a MySQL database containing pictures? I'm new to PHP and MySQL so I appreciate some directions--I've follow that tutorial on forms, and am learning about connecting to a database and getting info out of it. I hope to learn by executing simple codes on the server.

---

### Post by dazman19 on 2012-01-22
Its easier to store the data in a folder on the server. and a link to it in the database, its faster too.. 

However, if you want to insert the file into the database, there are a couple of things you need to know.

1) you need to make sure you create the right size blob column in the table. (mediumblob is 16MB i think, and this should be sufficent. So i would either resize the image if it is bigger than 16 MB or tell the user they cant upload a file that large. You also need to ensure the MAX_ALLOWED_PACKET size in MySQL is 16MB.

2) use file_get_contents to pick up the $_FILES['name']['tmp_name'] file. 


e.g. 

[PHP]
<?php 
$fileSize = filesize($_FILES['img']['tmp_name']);
$fileMimeType = $_FILES['img']['type'];
if( filesize  < 16777216) { 
   $fileContents = mysql_real_escape_string(file_get_contents($_FILES['img']['tmp_name']));
$fileName = mysql_real_escape_string($_FILES['img']['name']);
mysql_query("INSERT INTO `image` (`imagename`,`imagesize`, `imagecontents`, `imagemimetype`) VALUES ('$fileName','$fileSize','$fileContents','$fileMimeType')");
//some more code... 

}

?>


[/PHP]
YOu might not need to use filesize i think it is stored in the $_FILES array.
3) remember to set the upload on the form to meta.
4) you will need to store the mimetype aswell to serve the image again. 

5) when you serve the file at a later stage, you need to write the correct header, and content length. So you need the mimetype.

Above code is scribble, i just wrote it now, so might have a couple of errors, but i am sure you can figure it out.

---

### Post by epicoder on 2012-01-22
Gah! [Don't use W3Schools as a reference!](http://w3fools.com)

php.net has a [useful guide](http://us3.php.net/manual/en/features.file-upload.post-method.php) on handling file uploads through an html form.

---

### Post by |{urse on 2012-01-22
Why exactly is w3schools bad? I use their tuts all the time.

Edit: Huh just clicked that link, and after reading all that I think whoever made that site already improved w3 on most all the things they complained about (denoted with a strike-through). Is w3 good enough for you now?

---

### Post by epicoder on 2012-01-22
> **|{urse said:**
> I think whoever made that site already improved w3 on most all the things they complained about

Unfortunately, you are wrong. W3Schools has only fixed a small subset of the problems mentioned on W3Fools; the majority remain uncorrected. Also:
[QUOTE=W3Fools]W3Schools.com is **not affiliated with the W3C in any way**. Members of the W3C have asked               W3Schools to explicitly disavow any connection in the past, and they have refused to do so. [/QUOTE]
This by itself would cause me to doubt W3Schools, the horrendous amount of mistakes only cements that suspicion.

---

### Post by |{urse on 2012-01-22
man.. the more I read this the more I see what you're saying, I've only used w3s for the most basic of tuts personally.. Will stow (stow, not stop) linking to w3schools for a bit and consider the foundation on which most all of my html/css skills were developed. Thanks.

---

### Post by coffee412 on 2012-01-22
> **anon0 said:**
> How would you add the functionality of allowing data uploads in the form of pictures? What kind of structure should be used by the server to store the pics? Assume the server is LAMP based. Thanks!

Install apache web server if not already. Setup your security. Install Joomla and a mod that basically is going to do that for you. 

Alot for so little? Maybe. But your going to learn alot. Not that hard. Also you will find other mods thru joomla and they can be quite fun.

Have at it.
:D

---

### Post by |{urse on 2012-01-23
+1 @ joomla, superduper easy

---

