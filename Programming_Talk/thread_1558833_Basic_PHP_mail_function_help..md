---
title: "Basic PHP mail function help."
date: 2010-08-22
forum: Programming Talk
---

### Post by JustChris21 on 2010-08-22
Hi peeps, im a newb to PHP and canot understand why my script is not working properly. 
 
my code is

```
<?php
if (isset($_REQUEST['email'])){
    $to = "my@email.com";
    $subject = "Contact Form Enquiry";
    $message = $_REQUEST["message"];
    $from = $_REQUEST["email"];
    mail($to,$subject,$message,$from);
    header('Location:/thanks.php');}
else{
header('Location:/error.php');I 
exit();
}
?>
```The email sends fine. However the problem is the bit where I ask if the email bit is not filled in it should redirect to the page 'error.php', if it is not filled in it just sends the email and redirects to the 'thanks.php' page.

Any help appreciated.

---

### Post by Bachstelze on 2010-08-23
You probably want

[php]<?php
if (isset($_REQUEST['email']) && $_REQUEST['email'] != '') {
    $to = "my@email.com";
    $subject = "Contact Form Enquiry";
    $message = $_REQUEST["message"];
    $from = $_REQUEST["email"];
    mail($to,$subject,$message,$from);
    header('Location:/thanks.php');
} else {
header('Location:/error.php');I 
exit();
}
?>
[/php]

---

### Post by JustChris21 on 2010-08-23
Thank you!

---

### Post by Hellkeepa on 2010-08-27
HELLo!

I *strongly* recommend using a pre-build mailing module for this, as the code above is *completely* open to any kind of abuse!

Happy codin'!

---

