---
title: "sending mail with php"
date: 2005-12-25
forum: Programming Talk
---

### Post by grim918 on 2005-12-25
how do you send mail with php. im trying to code a user registration script that will send an e-mail for verification.
from what i know, php has the mail();
this is how im using my mail function

mail($recipient,$subject,$msg,$mailheaders);

everything seems to be ok but i read that you have to go into the php.ini file
and make some changes. does anyone know what changes need to be made.

---

### Post by sapo on 2005-12-25
[QUOTE=grim918]how do you send mail with php. im trying to code a user registration script that will send an e-mail for verification.
from what i know, php has the mail();
this is how im using my mail function

mail($recipient,$subject,$msg,$mailheaders);

everything seems to be ok but i read that you have to go into the php.ini file
and make some changes. does anyone know what changes need to be made.[/QUOTE]
I never had to configure anything, just make sure your sendmail is working properly, and the mail function should work.

btw..

[http://www.php.net/manual/en/ref.mail.php](http://www.php.net/manual/en/ref.mail.php)

---

### Post by grim918 on 2005-12-26
how do i check if sendmail is working properly and if its not how can i fix it. when i run my scripts i dont get any type of errors it executes without problems but when i check the mailbox that i want to send the message to i dont get nothing. i think that i might have a problem with sendmail. thanks for your help

---

### Post by grim918 on 2005-12-27
ok i got it working.i had to sudo apt-get install sendmail.
i thought that sendmail was installed by default. thanks for the help.

---

