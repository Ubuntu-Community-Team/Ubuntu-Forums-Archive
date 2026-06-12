---
title: "how to add css to .php file??"
date: 2009-08-08
forum: Programming Talk
---

### Post by kuldeepsidhu on 2009-08-08
plz give me some php knowledge..i ll be thankful to you..sir.. i have to include css files in my php file...how to do this..i am beginner..so plz tell me step by step..i have files index.php,header.php..i want to change the font color in the header.php file..how to do.it.?

---

### Post by Dill on 2009-08-08
Wherever you print the HTML header (perhaps in your *header.php* file?), you'll want to print a link to the stylesheet using *echo* or *print*:

[PHP]echo "<link rel='stylesheet' type='text/css' href='stylesheet.css' />";[/PHP]

You can also use the HTML [style tag]("http://www.w3schools.com/TAGS/tag_style.asp") to include inline CSS, but including your CSS in an external file is usually preferred

Is that what you mean?

Cheers,
Dill

---

### Post by kuldeepsidhu on 2009-08-08
i dont understand this..inline css is implemented right..but if we have to apply external css...where i have to put css file....in which folder where header.php exists or where index.php exists..?tell me in detail ..can you show me the directory structure...

---

### Post by Dill on 2009-08-08
It depends on the directory structure you've set up. If a stylesheet called *stylesheet.css* is in the **same directory** as *header.php*, you'll want to include this:

[PHP]echo "<link rel='stylesheet' type='text/css' href='stylesheet.css' />";[/PHP]

If you have all of your external CSS in a directory **below** header.php (let's call the directory *css*), you'll want to include this:

[PHP]echo "<link rel='stylesheet' type='text/css' href='css/stylesheet.css' />";[/PHP]

If you have your CSS file in a folder **above** header.php, you'll want to include this:

[PHP]echo "<link rel='stylesheet' type='text/css' href='../stylesheet.css' />";[/PHP]

Does that make sense?

Cheers,
Dill

---

### Post by ad_267 on 2009-08-08
> **kuldeepsidhu said:**
> i dont understand this..inline css is implemented right..but if we have to apply external css...where i have to put css file....in which folder where header.php exists or where index.php exists..?tell me in detail ..can you show me the directory structure...

You could just try both and see what works. Shouldn't take more than a minute. I'm pretty sure it would be relative to index.php.

---

### Post by Tibuda on 2009-08-08
The same way you do in (X)HTML. You can use whatever directory structure you want.

[php]<?php
// PHP code here
 ?>
<!doctype....>
<html>
<head>
<!-- HTML heading here /-->
<link rel="stylesheet" type="text/css" src="path/to/stylesheet.css" />
</head>
<body>
<!-- HTML body here /-->
<?php
// PHP code here
?>
</body>
</html>[/php]

---

