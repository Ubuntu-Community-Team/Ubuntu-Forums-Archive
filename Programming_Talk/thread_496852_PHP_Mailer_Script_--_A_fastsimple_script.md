---
title: "PHP Mailer Script -- A fast/simple script"
date: 2007-07-09
forum: Programming Talk
---

### Post by 7Priest7 on 2007-07-09
All my other posts have been questions
I decieded to try to give a little back...

This script I created for my site... (I did modify my info out)
```

<?php
$to = "User@Domain.ext"; // You
$subject = "Comment/Question"; // The Subject
$message = $_GET['comm']; // Assuming your form used get and the message is named "comm"
$from = "From: {$_GET['name']} <{$_GET['email']}>"; // From (the field named "name" and the email field named "email"
mail($to,$subject,$message,$from); // The Mail function at work
header("Location: http://www.Dos-Bible.org/"); // Redirect your user to a page of your choice
?>

```

I will show my actual form too for added ease
```

<form id="form" method="get" enctype="text/plain" action="Mail.php">
Name: <input name="name" type="text" id="name" /><br />
Email: <input name="email" type="text" id="email" /><br />
Comment/Question: <input name="comm" type="text" id="comm" /><br />
<input type="submit" value="Send" onclick="return Mail()" />
</form>

```

The Mail() function is just a few JavaScript Checks

You can see my script at work at [http://www.Dos-Bible.org/](http://www.Dos-Bible.org/)

Have Fun

Alex

---

### Post by 7Priest7 on 2007-07-09
I just changed the php mailer at my site...
Mine has a little more but it is pretty much the same...

Alex

---

