---
title: "Cookies"
date: 2011-02-13
forum: Programming Talk
---

### Post by hemoali on 2011-02-13
Please why I cannot set Cookie in linux with php codes

---

### Post by overdrank on 2011-02-13
Moved to General Help

---

### Post by s.fox on 2011-02-13
I think this would be better in [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39"), so I moved it :)

To set a cookie use the following code as an example:

```
<?php
$value = 'something from somewhere';
setcookie("TestCookie", $value);
?>
```To read the cookie later use the following code as example:

```

<?php
// Print an individual cookie
echo $_COOKIE["TestCookie"];
?>
```[COLOR=#000000][COLOR=#007700]

[COLOR=Black]If you still have problems please post your code so we can see where the problem is.

Hope this helps,

s.fox[/COLOR]
[/COLOR][/COLOR]

---

