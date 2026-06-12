---
title: "phpMailer problems."
date: 2007-08-25
forum: Programming Talk
---

### Post by jingo811 on 2007-08-25
Does this php file look OK to you?
I tested it a couple of times on my hotmail accounts previously and things seemed to work last week.  Then I did some more unsuccessful phpmail testing on those hotmail accounts from a more complicated php file with more classes.  
Today not even this simple php file works it just gives me
**Mail sending failed** 
error in Swiftfox do you know why this is happening when things worked last week?

[SIZE="4"]1.php[/SIZE]
```
<?php
// Include the phpmailer class
require('ThirdParty/phpmailer/class.phpmailer.php');

// Instantiate it
$mail = new phpmailer();

// Define who the message is from
**$mail->From = 'customer-smtp.one.com';**
$mail->FromName = 'Vicky';

// Set the subject of the message
$mail->Subject = 'Test Message';

// Add the body of the message
$body='This is a test';
$mail->Body = $body;

// Add a recipient address
$mail->AddAddress('vsuser02@hotmail.com', 'Victoria\'s Secret');

// Send the message
if(!$mail->Send())
    echo ('Mail sending failed');
else
    echo ('Mail sent successfully');
?>
```

---

### Post by jingo811 on 2007-08-26
Now I remember I could only run this kind of code directly from my Domain by FTP:ing the file to my Webhost account.
You can't test this kind of code on your own LAMP localhost, it just won't work.

[Problem solved]

---

