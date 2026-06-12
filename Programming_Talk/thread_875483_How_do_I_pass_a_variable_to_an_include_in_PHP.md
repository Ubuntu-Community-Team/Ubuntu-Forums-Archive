---
title: "How do I pass a variable to an include in PHP?"
date: 2008-07-30
forum: Programming Talk
---

### Post by tc101 on 2008-07-30
How do I pass a variable to an include in PHP?  For example in the two simple files below, how would I pass a variable from test.php to include.php?  I know how to do this with a form using $_POST, but I can't figure out how to do it in an include.

test.php

<html>
<body>
<b>first html</b>
<p>
<?php
include 'include01.php';
?>
<p>
<b>last html</b>
</body>
</html>

include.php

<?php
echo "this comes from the include";
?>

---

### Post by theY4Kman on 2008-07-30
Just define the variables you want to send before including the new file. Once included, the new file will be able to access those variables. For example:
[PHP]<?php
$var = "Hello, World!";
include("included.php");
?>[/PHP]
[PHP]<?php
// included.php
echo $var;
?>[/PHP]That will output:
```
Hello, World!
```

---

