---
title: "how to retain form data via the redirect page?"
date: 2011-05-30
forum: Programming Talk
---

### Post by ddmn on 2011-05-30
Hi,

How to retain the form data via redirect page? on the example below when  i submit, no form data is passed to either add.php or subtract.php.

How do i solve this problem?

index.html
```

<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<title>Insert title here</title>
</head>
<body>
<form action="redirect.php" method = "post">
 Number 1: <input type="text" name = "number1"><br>
 Number 2: <input type="text" name="number2"><br>
<input type="submit" name = "sel" value="add">
<input type="submit" name="sel" value="subtract">
</form>
</body>
</html>

```redirect.php
```

<?php
    switch ($_POST['sel']){
        //if we add
        case 'add':
            header("Location: add.php");
            break;
        //if we subtract    
        case 'subtract':
            header("Location: subtract.php");
            break;
    }
    //exit;
?>

```add.php
```


<?php

echo $_POST['number1']
." + ". $_POST['number2']." = "
. ($_POST['number1']+$_POST['number2']);

?>

```subtract.php
```

<?php

echo $_POST['number1']
." - ". $_POST['number2']." = "
. ($_POST['number1']-$_POST['number2']);

?>

```

---

### Post by satanselbow on 2011-05-30
sessions

---

### Post by ddmn on 2011-05-30
> **satanselbow said:**
> sessions

How do i accomplish that? I have been searching the internet and  can't get any help.

---

### Post by dazman19 on 2011-06-02
why would you do this. Just include it.

[PHP]<?php
    switch ($_POST['sel']){
        //if we add
        case 'add':
            include "Location: add.php";
            break;
        //if we subtract    
        case 'subtract':
            include "Location: subtract.php";
            break;
    }
    //exit;
?>[/PHP]

but to answer the question on sessions.

[PHP]<?php
session_set_cookie_params(600); //600 seconds
session_start();
    switch ($_POST['sel']){
        //if we add
        case 'add':
            $_SESSION['add'] = $_POST;
            header("Location: add.php");
            break;
        //if we subtract    
        case 'subtract':
            $_SESSION['subtract'] = $_POST;
            header("Location: subtract.php");
            break;
    }
    //exit;
?>[/PHP]

then in your other files. e.g. add.
[PHP]<?php
session_start(); //start the session
$_POST = $_SESSION['add'];
echo $_POST['number1']
." + ". $_POST['number2']." = "
. ($_POST['number1']+$_POST['number2']);
session_destroy();
?>[/PHP]

You need to call session_start() on each script to access the $_SESSION global.

---

