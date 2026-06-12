---
title: "php variable that is accessible in multiple files"
date: 2009-02-26
forum: Programming Talk
---

### Post by qmqmqm on 2009-02-26
Hi everyone

Is there a way to define some sort of "global" variable in php that is accessible to all php files in the project?

For example I have a variable "my_var" in 1.php file:

```
<html>
<head>
<script src="clienthint.js"></script> 
</head><body><form>
First Name:
<input type="text" id="txt1"
onkeyup="showHint(this.value)">
</form><p>Suggestions: <span id="txtHint"></span></p> </body>

<?php
	$my_var = "test";
?>
</html>
```

And I wish to use it 2.php:
```
<?php
$response="blah blah " . $my_var;
echo $response;
?>
```

Is there a way to do this?

Thanks,

Tom

---

### Post by cerealtx on 2009-02-26
only way i know how is to create a seperate php file with the values, and just include('filename.php') on each php page

---

### Post by Colonel Kilkenny on 2009-02-26
Or just put it into session. $_SESSION['foo'] = 'bar';
Just remember to initialize session in both files.

---

### Post by simeon87 on 2009-02-26
> **cerealtx said:**
> only way i know how is to create a seperate php file with the values, and just include('filename.php') on each php page

This would work when you want to share values that do not change (i.e., constants). The file 2.php will include the given filename but it won't have the value 1.php has constructed.

Perhaps an overview would be useful: a php file is executed whenever the user requests a page. When the code has ended, the state is lost so all calculations that were performed are not stored for later use by other php files (unless you're explicitly writing to a database or a file). In other words, there's no permanent state in php files that you're modifying, it's simply code that is executed each time the user requests a page.

---

### Post by qmqmqm on 2009-02-28
Thank you all very much. I think Ajax is way to go...

---

