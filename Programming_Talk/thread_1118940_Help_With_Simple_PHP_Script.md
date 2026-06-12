---
title: "Help With Simple PHP Script"
date: 2009-04-07
forum: Programming Talk
---

### Post by DGortze380 on 2009-04-07
Hey All,

Just learning PHP, and I've got to get this script working.

I've included the source below. It's a simple mail script to take input from an HTML form and send an e-mail. My problem is that I'm not getting anything in HTTP_POST_VARS[]. The array appears to be empty. I've tested it by just echoing to the screen, and nothing prints for any of the HTTP_POST_VARS variables I created.

Scripted down code snippets below:

HTML FORM
```

<html>
<head><title>Mail sender</title></head>
<body>
<form action="mail.php" method="post"> <b>Email</b><br /> <input name="email" size="40" type="text" />
<p><b>Subject</b><br /> <input name="subject" size="40" type="text" /></p>
<p><b>Message</b><br /> <textarea cols="40" rows="10" name="message"></textarea></p>
<p><input value=" Send " type="submit" /></p>
</form>
</body>
</html>

```


mail.php
```

<html>
<head><title>PHP Mail Sender</title></head>
<body>
<?php

/* All form fields are automatically passed to the PHP script through the array $HTTP_POST_VARS. */
$post_vars = $HTTP_POST_VARS;
$email = $post_vars['email'];
$subject = $post_vars['subject'];
$message = $post_vars['message'];
$headers = 'From: info@stewartsglobal.com' . "\r\n" .
    'Reply-To: info@stewartsglobal.com';
?>

<p>
  TO: <?php print($email); ?>
  <br>
  HEADERS: <?php print($headers); ?>
  <br>
  SUBJECT: <?php print($subject); ?>
  <br>
  MESSAGE: <?php print($message); ?>
  <br>
  
</p>

</body>
</html> 

```

---

### Post by DGortze380 on 2009-04-07
Sorry.

SOLVED

Old version of php on this server. Had to use _POST instead of HTTP_POST_VARS

---

### Post by v8YKxgHe on 2009-04-07
Btw, not an old version. $HTTP_POST_VARS is the old way of doing things, $_POST is the correct way to do things.

---

### Post by DGortze380 on 2009-04-07
> **AlexC_ said:**
> Btw, not an old version. $HTTP_POST_VARS is the old way of doing things, $_POST is the correct way to do things.

Correction. Old tutorial, new version of php. Had to use $_POST.

Thanks for the info.

---

### Post by v8YKxgHe on 2009-04-07
I'd advise stop reading what ever tutorial you are, since it is already teaching you bad and incorrect practices.

Personally I recommend [http://devzone.zend.com/node/view/id/627](http://devzone.zend.com/node/view/id/627) to beginners, however some parts of it are a little outdated, though it does teach you good practices (at least from what I saw glancing over it).

---

