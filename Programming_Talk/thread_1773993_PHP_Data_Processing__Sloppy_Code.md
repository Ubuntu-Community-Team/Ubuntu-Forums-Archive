---
title: "PHP Data Processing / Sloppy Code"
date: 2011-06-02
forum: Programming Talk
---

### Post by dhtseany on 2011-06-02
Hi ya'll,

Trying to clean up some really bulky PHP pages. Can someone take a quick peek at my code and tell me if what I've made will work? So far, I submit the form data (which does load correctly on the initial page load, per-form.php) but from there my 'if' statements don't seem to be working right.

Go ahead, be brutal ;)

Peace,
Sean

```

<?php
session_start();
if(isset($_SESSION['perdata'])) {
	$perdata = $_SESSION['perdata'];
	include('include/forms/per-edit.php');}
	else {
			if(isset($_POST['submit'])){
				include('include/forms/per-array.php');
				$_SESSION['perdata'] = $perdata;
				echo "<META HTTP-EQUIV='Refresh' Content='0; URL=start_per_conf.php'>";}
				else {
					include('include/forms/per-form.php');}}
?>

```

---

### Post by Petrolea on 2011-06-03
> **dhtseany said:**
> Hi ya'll,

Trying to clean up some really bulky PHP pages. Can someone take a quick peek at my code and tell me if what I've made will work? So far, I submit the form data (which does load correctly on the initial page load, per-form.php) but from there my 'if' statements don't seem to be working right.

Go ahead, be brutal ;)

Peace,
Sean

```

<?php
session_start();
if(isset($_SESSION['perdata'])) {
	$perdata = $_SESSION['perdata'];
	include('include/forms/per-edit.php');}
	else {
			if(isset($_POST['submit'])){
				include('include/forms/per-array.php');
				$_SESSION['perdata'] = $perdata;
				echo "<META HTTP-EQUIV='Refresh' Content='0; URL=start_per_conf.php'>";}
				else {
					include('include/forms/per-form.php');}}
?>

```

Well, the conditions are correct, but what exactly goes wrong? It's really hard to tell just like that. If there is no session variable first 'if' won't execute, and second one won't execute if the button hasn't been pressed.

Maybe reverse something? Second if will get executed if session var doesn't exist. And if you include some third page while trying to get to second 'if', it will never reach it (since a new page will get loaded). But as I said, I can't tell much from this piece of code.

---

