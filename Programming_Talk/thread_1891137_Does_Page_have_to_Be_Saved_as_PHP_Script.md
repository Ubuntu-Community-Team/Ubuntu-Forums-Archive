---
title: "Does Page have to Be Saved as PHP Script?"
date: 2011-12-05
forum: Programming Talk
---

### Post by dodle on 2011-12-05
I have a site on Sourceforge and the only way I can get PHP scripts to work inside my HTML code is to save the page with .php file extension. Is this normal?

[php]<html>
<head>
<title>Testing PHP</title>

</head>

<body>
<?php
echo "Hello World!";
?>

</body>
</html>[/php]

If I save it as "test.html" or just as "test", I get a blank page. If I save it as "test.php" it displays "Hello World!".

---

### Post by Bachstelze on 2011-12-05
Yes it is normal. The .php extension is what tells the server to parse it with PHP, otherwise the page is treated as pure HTML, and the PHP tags act as comments.

---

### Post by dodle on 2011-12-05
Okay, thanks. Then can I access functions and variables of an external php script from an html file or does my html file have to have a .php extension as well?

hello.php
[php]<?php
$hello = "Hello World!";
?>[/php]

hello.html
[php]<html>
<head>
<title>Hello</title>
</head>

<body>
<!-- show $hello here -->
</body>
</html>[/php]

Sorry, I'm just getting into web programming and I'm having a hard time understanding it.

---

### Post by Bachstelze on 2011-12-05
If your file uses anything PHP, you need the .php extension. Also, if you want to use variables defined in one file in another file, you have to include the file where the variables are defined. See the examples in [http://php.net/manual/en/function.include.php](http://php.net/manual/en/function.include.php)

---

### Post by dodle on 2011-12-05
Thank you, very helpful.

---

