---
title: "&lt;?php include(&quot;header.php&quot;; ?&gt; not working please help!"
date: 2008-01-19
forum: Programming Talk
---

### Post by lucas4ce on 2008-01-19
Ok I have ubuntu 7.10 desktop with Apache 2 web server, PHP5 is installed.  In my html page I want to insert a standard header and have something like the following..

<table>
<tr>
<td colspan="3"><?php include("header.php"); ?></td>
</tr>
<tr>
<td>stuff here</td>
<td>stuff here</td>
<td>stuff here</td>
</tr>
</table>

I've followed the advise here [https://help.ubuntu.com/community/ServerSideIncludes](https://help.ubuntu.com/community/ServerSideIncludes) and i get the local time when I open ssi-test, so I assume SSI is working fine.

I get no errors when opening the html page but the contents of header.php does not appear.

Any ideas?

---

### Post by LaRoza on 2008-01-19
> **lucas4ce said:**
> Ok I have ubuntu 7.10 desktop with Apache 2 web server, PHP5 is installed.  In my html page I want to insert a standard header and have something like the following..

<table>
<tr>
<td colspan="3"><?php include("header.php"); ?></td>
</tr>
<tr>
<td>stuff here</td>
<td>stuff here</td>
<td>stuff here</td>
</tr>
</table>

I've followed the advise here [https://help.ubuntu.com/community/ServerSideIncludes](https://help.ubuntu.com/community/ServerSideIncludes) and i get the local time when I open ssi-test, so I assume SSI is working fine.

I get no errors when opening the html page but the contents of header.php does not appear.

Any ideas?

Try using "require()" instead of "include()". Require will give error messages.

---

### Post by lucas4ce on 2008-01-19
Thanks for the reply!

Ok I'm using require now, but still no errors on the page and no header.php

---

### Post by LaRoza on 2008-01-19
> **lucas4ce said:**
> Thanks for the reply!

Ok I'm using require now, but still no errors on the page and no header.php

What is the contents of header.php?

---

### Post by lucas4ce on 2008-01-19
So far I'm just trying to get it working, I've tried the following:

sometext

-and-

"sometext"

-and-

<?php
echo "sometext"
?>

not really sure how to format the header.php file tbh

---

### Post by lucas4ce on 2008-01-19
I just changed the php file name to a file that does not exist..

for example...require("nofile.php"); ?>

still no errors on the page.

Seems the browser is simply ignoring the php commands, this isthe case in IE and firefox.  So I'm guesing its something to do with my config?

---

### Post by LaRoza on 2008-01-19
> **lucas4ce said:**
> I just changed the php file name to a file that does not exist..

for example...require("nofile.php"); ?>

still no errors on the page.

Seems the browser is simply ignoring the php commands, this isthe case in IE and firefox.  So I'm guesing its something to do with my config?

It has nothing to do with the browser, it takes place on the server, which leads me to my next question...

Do you have Apache and PHP installed, and are the documents being served by them?

---

### Post by lucas4ce on 2008-01-19
Hi,

yes apache and PHP are installed, I can view [http://mydomain/header.php](http://mydomain/header.php) perfectly.

---

### Post by Sam on 2008-01-19
Try using
```
error_reporting(E_ALL);
```
before the inclusion.

---

### Post by lucas4ce on 2008-01-19
Hi Sam,

do you mean like this?

<td colspan="3"><?php error_reporting(E_ALL); require("header.php"); ?></td>

cos that made no difference also sadly.

---

### Post by Sam on 2008-01-19
And what does:```
var_dump(is_readable('header.php'));
```
And:```
echo ini_get('include_path');
```

---

### Post by lucas4ce on 2008-01-19
ok the line now reads

<td colspan="3"><?php var_dump(is_readable("header.php")); echo ini-get('include_path'); error_reporting(E_ALL); require("header.php"); ?></td>


still nothing I'm afraid.

---

### Post by Sam on 2008-01-19
Sorry I was unclear. Use this code[php]
<?php
var_dump(is_readable('header.php'));
echo ini_get('include_path');
?>
[/php]
on the top of index.php.

---

### Post by lucas4ce on 2008-01-19
ok I created an index.php file and entered the code.

I get this output..

bool(true) .:/usr/share/php:/usr/share/pear

---

### Post by Sam on 2008-01-19
Weird... I'm out of ideas.

Try this (focus on the problem, don't put anything else in these files):

index.php
```
<?php require('header.php'); ?>
<p>This is index.php</p>
```

header.php
```
<p>This is header.php</p>
```

---

### Post by aks44 on 2008-01-19
This strikes me:

> **lucas4ce said:**
> In my html page I want to insert a standard header

What is your original page's extension? From the various answers you gave, it looks like it is not a .php...

---

### Post by lucas4ce on 2008-01-19
Well thanks for continuing to help me!

That worked!  I get this from index.php

This is header.php

This is index.php


The php files are read fine it seems when I open them from mydomain/index.php.  But if I try to to open them locally I'm prompted to open or save the file, I had this problem previously when php wasn't parsing.  Does this help at all?

---

### Post by Sam on 2008-01-19
They need to be parsed by PHP, so opening a php file with Firefox don't work. Put the files in /var/www (default apache directory), assuming you properly installed apache+php. Then access your project with [http://localhost/index.php](http://localhost/index.php)

---

### Post by lucas4ce on 2008-01-19
> **aks44 said:**
> This strikes me:



What is your original page's extension? From the various answers you gave, it looks like it is not a .php...


It was .html, but guessing your next comment I changed it .php and now it works!!!!

Thank you!!!

---

### Post by aks44 on 2008-01-19
> **lucas4ce said:**
> It was .html, but guessing your next comment I changed it .php and now it works!!!!

Well despite the fact that you already guessed it, I'll say it anyway...

PHP files need to have a .php extension for them to be parsed & executed correctly through Apache.

Sam's previous post also has very useful advice.

---

### Post by Sam on 2008-01-19
If you need to include an html file, use the [readfile()](http://www.php.net/function.readfile) function.

---

### Post by lucas4ce on 2008-01-19
Thank you both!!!  Excellent advise!!  Sorry if I wasted anyones time with a silly error!

So just out of interest if I'm going to use the php include/require commands in a page, that page has to be a .php file.

And if the file I'm including has only html in it and is a .html file, then I can use readfile() instead?

---

### Post by LaRoza on 2008-01-19
> **lucas4ce said:**
> Thank you both!!!  Excellent advise!!  Sorry if I wasted anyones time with a silly error!

So just out of interest if I'm going to use the php include/require commands in a page, that page has to be a .php file.

And if the file I'm including has only html in it and is a .html file, then I can use readfile() instead?

The PHP files need to be executed. You can have apache do this with any file extension, but the defaults are .php and .php5.

---

### Post by Sam on 2008-01-19
> **lucas4ce said:**
> And if the file I'm including has only html in it and is a .html file, then I can use readfile() instead?

.html or whatever, readfile() just dumps the content of the file to the output.

---

