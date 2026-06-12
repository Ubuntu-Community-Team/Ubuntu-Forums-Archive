---
title: "Is this an injection attack?"
date: 2009-10-25
forum: Programming Talk
---

### Post by pytheas22 on 2009-10-25
This isn't an Ubuntu-specific question, but I'm hoping someone here might be able to help me out all the same.

I have a public website, coded in PHP, that allows visitors to send email via a form.  The code that sends the email is located in a file named 'send_mail.php' and looks like this:

```
<?php
$to = 'recipient1@address.com' . ', ';
$to .= 'recipient2@address.com' . ', ';
$to .= 'recipient3@address.com' . ', ';

$subject = "Mail from website";
$message = $_POST["message"];
$sender_email = $_POST["sender_email"];
$sender_name = $_POST["sender_name"];
$message = "You have received the following message from $sender_name, $sender_email, via the website: $message";
mail($to, $subject, $message);
$mail_success = "yes";

include "contact.php";

?>

```

'contact.php' includes this HTML:
```

  	<p><strong>Use this form to send email:</strong></p>
  <form method="post" enctype="multipart/form-data" action="send_mail.php">
    <p><input class="side" type="text" value="your name" name="sender_name" /></p>
    <p><input class="side" type="text" value="your email"  name="sender_email" /></p>
    <p><textarea class="side" name="message" cols="70" rows="10"></textarea></p>
    <p><input class="button" value="Send" type="submit" /></p>
    <p><input class="button" value="Reset" type="reset" /></p>
  </form>
```

Recently, I've been getting a number of emails from the website that contain the following:
```

login solidarity%0A%0aadd $sender_email $sender_name%0A%0aend
```

and nothing else.  I'm a bit puzzled about why these are appearing.  Over the last year, I've been receiving one or two a month and didn't think much of them, but in the last week I've been getting several a day.  I'm worried that someone may be trying to do something nasty, like HTML injection.  But I'm also not much of a programmer, so maybe this has a less sinister explanation that will be obvious to people with more programming experience.  If anyone has any thoughts, I'd really appreciate them, and thanks in advance for engaging in a non-Ubuntu topic.

---

### Post by wmcbrine on 2009-10-26
Dunno, but it kinda looks more like a broken spambot. Whether that's "less sinister", I'll leave up to you.

---

### Post by NoaHall on 2009-10-26
I'd add a validation system to make sure none of the fields are blank, and that the email address is in the right format.

---

### Post by pytheas22 on 2009-10-26
Thanks for the helpful suggestions.  A broken spambot makes a lot of sense.  I'll see if adding a simple captcha test solves the problem.  I'll also add code to validate email addresses and check for blank fields; I'm sure that won't hurt.

---

