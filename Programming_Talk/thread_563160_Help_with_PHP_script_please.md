---
title: "Help with PHP script please?"
date: 2007-09-29
forum: Programming Talk
---

### Post by Peter1234123 on 2007-09-29
I have a login script, in PHP, that an HTML document refers to, to validate login info...but, I can't recall the source to redirect to a page if the info is correct..here's the source thus far: 
```
<?php
$username = $_POST['username'];
$password = $_POST['password'];
echo "<pre>";
echo "--You entered this information--\n";
echo "Username: $username\nPassword: $password\n\n";
if (($username == "php") && ($password = "rocks")) {
	echo "You submitted the correct username/password combination.";
} else {
echo "The username and password submitted were invalid.  Please try again.\n";
	echo "<a href=\"login.html\">Click here to go back.</a>";
}
```

---

### Post by michaelzap on 2007-09-29
header('Location: [http://www.example.com/');](http://www.example.com/');)

[More info here.]("http://www.php.net/manual/en/function.header.php")

---

### Post by Peter1234123 on 2007-09-29
Thanks :)

---

### Post by Compyx on 2007-09-29
> **Peter1234123 said:**
> 
<snip>
[PHP]if (($username == "php") && ($password = "rocks"))[/PHP]
<snip>

Whatever password the user enters, it'll always be correct, since
[php]$password = "rocks"[/php] always yields true. You probably meant to write:
[php]$password == "rocks"[/php]
;)

---

