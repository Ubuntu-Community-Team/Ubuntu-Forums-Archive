---
title: "HTML / PHP Question"
date: 2010-05-10
forum: Programming Talk
---

### Post by Krupski on 2010-05-10
Hi all,

I hope this post is OK considering it really has nothing to do with Ubuntu... but it IS a programming question, so here goes:

I need to be able to upload files to my web server using a "file" select box and PHP to handle the upload.

Both my HTML code and PHP code work, but there is one problem that I just can't seem to solve!

The HTML file will give me the "Browse" function, I select the file to upload, the "submit" calls the PHP code and the file successfully uploads. BUT, then it just sits there!

I can't figure out how to return to the original HTML caller!

So, my question is, how do I setup the PHP file so that it "exits" when it's done?

For example, (using BASIC as an analogy), I want to do this:

HTML
GOSUB PHP
MORE HTML
...
...
...
PHP
UPLOAD_FILE
RETURN


But what it's doing now is more like this:

HTML
GOTO PHP
MORE HTML
...
...
...
PHP
UPLOAD_FILE
STOP

You see... "MORE HTML" never gets run!



Any ideas will be greatly appreciated!

-- Roger

---

### Post by Bachstelze on 2010-05-10
It would be better if you just pasted your code, I think.

---

### Post by soltanis on 2010-05-10
Okay, first of all, PHP is a preprocessed language; i.e. all PHP code is executed before client side HTML is rendered. Technically speaking, then, it has already exited when the client receives the web page.

If you upload a file to PHP, then you are simply invoking a CGI-like call; your browser submits the file via HTTP POST (or GET depending on how you configure your forms) and the server invokes your PHP code to handle the uploaded file.

You should really show us your code to tell us what you mean.

---

### Post by Krupski on 2010-05-10
> **soltanis said:**
> You should really show us your code to tell us what you mean.

**Bachstelze** and **soltanis** yeah sorry I should have posted the code. Here it is:

The HTML part:
```

<html>

<head>
</head>

<body>
 <form enctype="multipart/form-data" action="upload.php" method="post">
Please choose a file:
  <input size="30" name="uploaded" type="file">
  <input type="submit" value="Go!">
 </form>
</body>

</html>

```


The PHP part:
```

<?php
{
  $target = "upload/";
  $target = $target . basename($_FILES['uploaded']['name']);
  {
    if(move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
    {
      echo "The file ". basename( $_FILES['uploadedfile']['name']). " has been uploaded";
    }
    else
    {
      echo "Upload failed";
    }
  }
}
?>

```


I know the PHP code does absolutely no checking for file size or file type... I'm just trying to get it to WORK at this point.

Thanks for the help and I look forward to your comments.

-- Roger

---

### Post by roccivic on 2010-05-11
You mean something like this?

[PHP]<html>
<head>
</head>
<body>
 <form enctype="multipart/form-data" action="?action=upload" method="post">
Please choose a file:
  <input size="30" name="uploaded" type="file">
  <input type="submit" value="Go!">
 </form>
<?php
if ( $_GET['action'] == 'upload' ) {
	$target = "upload/";
	$target = $target . basename($_FILES['uploaded']['name']);
	if( move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
		echo "The file ". basename( $_FILES['uploaded']['name']). " has been uploaded";
	else
		echo "Upload failed";
}
else {
	echo "Please select a file to upload...";
}
?>
</body>
</html>[/PHP]

---

### Post by Krupski on 2010-05-11
> **roccivic said:**
> You mean something like this?

[PHP]<html>
<head>
</head>
<body>
 <form enctype="multipart/form-data" action="?action=upload" method="post">
Please choose a file:
  <input size="30" name="uploaded" type="file">
  <input type="submit" value="Go!">
 </form>
<?php
if ( $_GET['action'] == 'upload' ) {
	$target = "upload/";
	$target = $target . basename($_FILES['uploaded']['name']);
	if( move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
		echo "The file ". basename( $_FILES['uploaded']['name']). " has been uploaded";
	else
		echo "Upload failed";
}
else {
	echo "Please select a file to upload...";
}
?>
</body>
</html>[/PHP]

I just tried the code above. I put it into a file called "index.html" and ran it on my Ubuntu LAMP server. It prompts but doesn't upload. I thought then "hmmm maybe it needs to be named "index.php"" so I tried that. Still nothing.

What am I missing?

---

### Post by trent.josephsen on 2010-05-11
> **Krupski said:**
> I just tried the code above. I put it into a file called "index.html" and ran it on my Ubuntu LAMP server. It prompts but doesn't upload. I thought then "hmmm maybe it needs to be named "index.php"" so I tried that. Still nothing.

What am I missing?

What does the source of the retrieved document look like?  i.e. when you go to View > Page Source or press Ctrl-U in Firefox, what do you see?

---

### Post by Krupski on 2010-05-11
> **trent.josephsen said:**
> What does the source of the retrieved document look like?  i.e. when you go to View > Page Source or press Ctrl-U in Firefox, what do you see?

Here is a cut-n-paste from Firefox "View Page Source":

```

<html>
<head>
</head>
<body>
 <form enctype="multipart/form-data" action="?action=upload" method="post">
Please choose a file:
  <input size="30" name="uploaded" type="file">
  <input type="submit" value="Go!">
 </form>
<?php
if ( $_GET['action'] == 'upload' ) {
    $target = "upload/";
    $target = $target . basename($_FILES['uploaded']['name']);
    if( move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
        echo "The file ". basename( $_FILES['uploaded']['name']). " has been uploaded";
    else
        echo "Upload failed";
}
else {
    echo "Please select a file to upload...";
}
?>
</body>
</html>

```

If it means anything, the PHP part is all syntax colored a light purple (see screenshot):

[IMG]http://three-dog.homelinux.com/upload/screenshot.png[/IMG]

It "acts" like it's working in that to upload a 6MB file, it's "busy" for about 1 second or so... but the file does not end up in './upload'.

Before you say AH-HA the file is too large!.... I adjusted the max upload size in PHP.INI to 16MB because it's limited to 2MB "out of the box" and I needed more and indeed it does work fine with my message board and larger-than-2MB uploads.

Any ideas what the heck I'm doing wrong I would appreciate.

P.S. I also tried various permissions on the HTML file... chown to www-data:www-data, to root:root, chmod to 0755, 0644... nothing makes any difference.

I'll bet it's something absurdly simple that I'm missing...

Thanks for the reply... please let me know if you have any ideas.

-- Roger

---

### Post by ju2wheels on 2010-05-11
You should not be able to see that php on the browser side. That means your webserver is not configured properly to parse and execute the php code. Meaning you dont have php installed/configured properly or Apache doesnt know what to do with the .php extension because you havent told it.

Your should have something like this being included by apache:

```

$ cat /etc/apache2/mods-enabled/php5.conf 
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

Edit: Actually I just noticed you were showing the source for an HTML file so that explains that, ignore my above comment. Either way I think what you want to be doing is printing the resulting page you want to be shown after the upload or doing a Location redirect to the proper page.

---

### Post by Krupski on 2010-05-11
> **ju2wheels said:**
> You should not be able to see that php on the browser side. That means your webserver is not configured properly to parse and execute the php code. Meaning you dont have php installed/configured properly or Apache doesnt know what to do with the .php extension because you havent told it.

Your should have something like this being included by apache:

```

$ cat /etc/apache2/mods-enabled/php5.conf 
<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

Edit: Actually I just noticed you were showing the source for an HTML file so that explains that, ignore my above comment. Either way I think what you want to be doing is printing the resulting page you want to be shown after the upload or doing a Location redirect to the proper page.

I believe the web server is properly configured since I run a PHP based message board that works just fine.

And based on what you said, I tried something. I saved the code to "index.php" instead of "index.html" and it worked!

What's strange is I did this before and it didn't work... so I must have done something wrong the first time but I don't know what.

Anyway, here's what the "View Source" looks like now:

```

<html>
<head>
</head>
<body>
 <form enctype="multipart/form-data" action="?action=upload" method="post">
Please choose a file:
  <input size="30" name="uploaded" type="file">
  <input type="submit" value="Go!">
 </form>
Please select a file to upload...</body>
</html>

```

But the actual source (on disk) is:

[PHP]
<html>
<head>
</head>
<body>
 <form enctype="multipart/form-data" action="?action=upload" method="post">
Please choose a file:
  <input size="30" name="uploaded" type="file">
  <input type="submit" value="Go!">
 </form>
<?php
if ( $_GET['action'] == 'upload' ) {
    $target = "upload/";
    $target = $target . basename($_FILES['uploaded']['name']);
    if( move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
        echo "The file ". basename( $_FILES['uploaded']['name']). " has been uploaded";
    else
        echo "Upload failed";
}
else {
    echo "Please select a file to upload...";
}
?>
</body>
</html>
[/PHP]


So now it works, but I have the same problem... it says "The file xxx has been uploaded" but then it sits there. I need to do something AFTER the PHP upload is finished and that's what I don't know how to do.

---

### Post by ju2wheels on 2010-05-12
What exactly is it that you want to do after the file gets uploaded? What is the output or action you are expecting...

All you have to do is print out what you want for HTML instead of printing "The file X has been uploaded" or change up your code a little so you are able to do a page redirect instead.

---

### Post by roccivic on 2010-05-12
You can use meta tags to redirect the user (it's cross-browser and all that). Otherwise you can use the location header: [http://php.net/manual/en/function.header.php](http://php.net/manual/en/function.header.php) (I'm not a fan of the latter).

[PHP]<html>
<head>
</head>
<body>
<?php
if ( $_GET['action'] == 'upload' ) {
	$target = "./";
	$target = $target . basename($_FILES['uploaded']['name']);
	if( move_uploaded_file($_FILES['uploaded']['tmp_name'], $target))
		echo "The file ". basename( $_FILES['uploaded']['name']). " has been uploaded";
	else
		echo "Your upload has failed.";
	echo "<p>Please wait while you are redirected...";
	echo "<meta http-equiv=\"refresh\" content=\"3; url=http://www.google.ie/\">";
}
else {
?>
	<form enctype="multipart/form-data" action="?action=upload" method="post">
	Please choose a file:
	<input size="30" name="uploaded" type="file">
	<input type="submit" value="Go!">
	</form>
	Please select a file to upload...
<?php
}
?>
</body>
</html>[/PHP]

If this still does not help, then you must specify more precisely what you want.

---

