---
title: "[SOLVED] PHP posting data from a redirect page"
date: 2008-06-09
forum: Programming Talk
---

### Post by mike_g on 2008-06-09
Is it possible to post data from a page using a redirect? As the redirect has to come before the html I can't put a form in it. Ideally I'd like to be able top do this w/o cookies. Heres some code it might explain better what I am trying to do:
```
<?PHP
	include('admin_functions.php');
	ToggleOrderDispatchState($_POST['id']);
	header('Location: order_details.php');[COLOR="DarkRed"]//<-I want to post the id back to this page.
[/COLOR]?>
```
Any suggestions?

Cheers.

---

### Post by decipher on 2008-06-09
Not sure if you can do that.. although i'm not certain.

Hmm if it's just an id that's being POSTed, why not add it to the URL and use GET?
[php]
<?PHP
	include('admin_functions.php');
	ToggleOrderDispatchState($_POST['id']);
	header('Location: order_details.php?id='.$_POST['id']);
?>
[/php]

---

### Post by mike_g on 2008-06-09
Thanks for that. I have been playing around with it for a bit, but I cant seem to be able to append the id variable to the location.
```
<?PHP
	include('admin_functions.php');
	$id = $_GET['id'];
	ToggleOrderDispatchState($id);
	header('Location: order_details.php?id='.$id); 
?>
```
the url comes up with "order_details.php?id=" and putting extra quote marks around it doesent seem to work either. Is there any other way to cause a redirect? Or is there some way to get thsi to work? 

Cheers.

---

### Post by decipher on 2008-06-09
Firstly, why are you using $_GET, when in the first example you use $_POST?

It is a good idea with debugging to set your error levels so you know why $id is blank:

Use error_reporting(E_ALL); and that should show you notice errors, eg variable not assign/does not exist.

Also, To view which values exist in your global arrays, use print_r();

eg
[php]
print_r($_POST);
print_r($_GET);
[/php]

[php]
<?PHP
	error_reporting(E_ALL);
	include('admin_functions.php');
	$id = $_POST['id'];
	ToggleOrderDispatchState($id);
	header('Location: order_details.php?id='.$id); 
?>
[/php]

order_details.php
[php]
<?php
die('ID: '.$_GET['id']);
?>
[/php]

---

### Post by mike_g on 2008-06-09
Actually that did work. My problem was that I forgot to set the calling page to use 'GET' when posting data. Cheers.

---

### Post by decipher on 2008-06-09
> **mike_g said:**
> Actually that did work. My problem was that I forgot to set the calling page to use 'GET' when posting data. Cheers.

Cheers :)

---

