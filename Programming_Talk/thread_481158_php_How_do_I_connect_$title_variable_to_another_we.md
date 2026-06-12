---
title: "php: How do I connect $title variable to another webpage?"
date: 2007-06-22
forum: Programming Talk
---

### Post by jingo811 on 2007-06-22
My **header.inc** file.
```
<!DOCTYPE HTML PUBLIC 
"-//W3C//DTD HTML 4.01//EN" 
"http://www.w3.org/TR/html4/strict.dtd">

<html lang="en">
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8">
<meta name="description" content="Den bästa bokhandeln som jag har gjort hittills!">
<meta name="keywords" content="film, filmer, billigt, ebutik">

<?php
**print "<title>" . $_REQUEST["$title"] . "</title>";**
?>

<style type="text/css" media="screen">
..
..
..
```

My **index.php** file.
```

<?php
[B]	$title = "PHP + CSS exempel";
	include "header.inc";[/B]
?>
..
..
..

```

I don't know exactly how to store the $title variable in index.php to get my heather.inc to grab the values in variable $title and print it out in my browser?
I'm reading in my nightcourse notes but so far I only find methods for making GET links and POST forms none of which seems to fit into this problem.  I'll continue searching for the answer in my notes and papers but would appreciate some guidance so I know what I should look for?

---

### Post by jingo811 on 2007-06-22
I'm guessing that I should use something like this with the date example?

```
<form method="POST" action="reciever.php">
**   <input type="hidden" name"datum"**
   value="<?php pring date("Y-m-d" ?>">
</form>
```

and then use $_REQUEST[datum] on the reciever.php webpage.

---

### Post by v8YKxgHe on 2007-06-22
You don't need to do $_REQUEST["$title"]; just do $title;

---

### Post by asmweb on 2007-06-22
Yep you just have to add to a simple variable the title name and then recall it at the header page!

string $title = "you title name";
include("header.inc");

--------------------------------------------
#header.inc
<html>
   <head>
     <title><?php echo($title); ?></title>
 </head>
 ----> some other code <----

</html>

---

### Post by v8YKxgHe on 2007-06-22
There's no need to do echo( $title ); - just echo $title will do

Also, with PHP you dont define the type of a var, as in you don't do "string $title" but just do $title = "your title name";

---

### Post by Bachstelze on 2007-06-22
And if you have short tags enabled, instead of

```
<?php echo($title); ?>
```

You can do

```
<?=$title; ?>
```

---

### Post by asmweb on 2007-06-22
well AlexC_ what you wrote are just details and i guess we are not running after those details ... important the core to be right!

---

### Post by v8YKxgHe on 2007-06-22
indeed, however by doing "string $var;" would lead to a syntax error. 

HymnToLife, you shouldn't really be using short-tags, afaik they are not enabled by default and so can cause issues if you need to move the script else where, it's always best habbit to do <?php ... instead of <?

---

### Post by jingo811 on 2007-06-22
hehe it worked Y...MCA 	\\:D/  *dances* tnx ppl.

---

