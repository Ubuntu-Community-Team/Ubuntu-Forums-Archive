---
title: "will someone please write me a php script"
date: 2006-07-13
forum: Programming Talk
---

### Post by %hMa@?b&lt;C on 2006-07-13
I have a HTML form that has $Email and $Body I would like I php4 script that simply sends an email to jeff.crowell[at]gmail[dot]com with the Subject as "contact form" and the body to say, "the users email is $Email, the users message is "$Body" Thanks!
-jeff

---

### Post by Ragazzo on 2006-07-13
[http://www.php.net/manual/en/function.mail.php]("http://www.php.net/manual/en/function.mail.php")

Something like this:

```

<?php

$email = $_POST['email'];
$body = $_POST['body'];

$message = "the users email is $email, the users message is:\n \"$body\"";
// In case any of our lines are larger than 70 characters, we should use wordwrap()
$message = wordwrap($message, 70);

if(mail("your@email.com', 'contact form', $message)) {
echo "thank you";
} else {
echo "something went wrong";
}
?>

```

---

### Post by %hMa@?b&lt;C on 2006-07-13
Thank you! Also, how do you do, if it was success, make the page reload to say, google.com?

---

### Post by Ragazzo on 2006-07-13
> **jeffc313 said:**
> Thank you! Also, how do you do, if it was success, make the page reload to say, google.com?

```

if($success) {
header("Location: http://www.google.com");
exit;
}

```

You shouldn't print any message if you do redirection.

---

