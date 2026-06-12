---
title: "php mail() not working on Ubuntu 11.10, LAMP stack"
date: 2011-10-24
forum: Programming Talk
---

### Post by 1cookie on 2011-10-24
hi

php mail() normally works out of the box for me. Especially with Ubuntu . Not at the moment it seems. :(

I'm using the following code:

```

<?php

// mail.php

$to      = 'myemail@yahoo.com';
$subject = 'test subject';
$message = 'hello this is a test';
$headers = 'From: webmaster@example.com' . "\r\n" .
    'Reply-To: webmaster@example.com';

if( mail($to, $subject, $message, $headers) ){

    echo 'Mail was sent';
} else {
    echo 'Couldn\'t send the mail';

```Ive tried allsorts:

tried this:

[http://www.blog.highub.com/javascript/javascript-core/make-ubuntu-php-localhost-mail-function-work/](http://www.blog.highub.com/javascript/javascript-core/make-ubuntu-php-localhost-mail-function-work/)

and

[http://email.about.com/od/emailprogrammingtips/qt/Configure_PHP_to_Use_a_Local_Mail_Server_for_Sending_Mail.htm](http://email.about.com/od/emailprogrammingtips/qt/Configure_PHP_to_Use_a_Local_Mail_Server_for_Sending_Mail.htm)


I checked my error.log file:

```

sh: /usr/sbin/sendmail: not found
[Mon Oct 24 17:48:48 2011] [notice] caught SIGTERM, shutting down
[Mon Oct 24 17:49:07 2011] [notice] Apache/2.2.20 (Ubuntu)  PHP/5.3.6-13ubuntu3.2 with Suhosin-Patch configured -- resuming normal  operations
sh: /usr/sbin/sendmail: not found
sh: /usr/sbin/sendmail: not found
[Mon Oct 24 18:04:52 2011] [notice] caught SIGTERM, shutting down
[Mon Oct 24 18:04:53 2011] [notice] Apache/2.2.20 (Ubuntu)  PHP/5.3.6-13ubuntu3.2 with Suhosin-Patch configured -- resuming normal  operations
sh: /usr/sbin/sendmail: not found
sh: /usr/sbin/sendmail: not found
[Mon Oct 24 18:18:51 2011] [notice] caught SIGTERM, shutting down
[Mon Oct 24 18:18:52 2011] [notice] Apache/2.2.20 (Ubuntu)  PHP/5.3.6-13ubuntu3.2 with Suhosin-Patch configured -- resuming normal  operations
sh: /usr/sbin/sendmail: not found
sh: /usr/sbin/sendmail: not found
sh: /usr/sbin/sendmail: not found


```So it appears that my config can't find sendmail. I'm no expert on this though?

The shell confirms:

```

andy@andy-R519-R719:/usr/sbin$ locate sendmail
/usr/lib/evolution-data-server/camel-providers/libcamelsendmail.so
/usr/lib/evolution-data-server/camel-providers/libcamelsendmail.urls
/usr/share/perl5/Mail/Mailer/sendmail.pm
andy@andy-R519-R719:/usr/sbin$ 


```

Emails aren't getting through!!

Can anyone offer some advice?

best

---

### Post by satanselbow on 2011-10-24
install sendmail?

```
sudo install apt-get sendmail
```

It does not seem to be installed on 11.10 by default - it may have been previously ;)

---

### Post by 1cookie on 2011-10-25
> **satanselbow said:**
> install sendmail?

```
sudo install apt-get sendmail
```It does not seem to be installed on 11.10 by default - it may have been previously ;)

Of course silly me. I was a little tired last night and I thought the PHP gods were conspiring against me. :)

Sendmail is now installed. I just ran the script and had a moment with Apache, it stopped working temporarily. 

error.log:

```

[Tue Oct 25 14:44:00 2011] [notice] caught SIGTERM, shutting down
[Tue Oct 25 15:00:09 2011] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations

```


OK the script now works but still no mail is sent??

---

### Post by satanselbow on 2011-10-25
Does the timestamp on the SIGTERM match the time you send the mail? They may not be related as they were appearing in your logs previously... might be a dodgy extension? (incorrect version?)

Might be an idea to turn all php errors on as well to see if there is something else in the script not behaving as it should ;)

Have you tried a vanilla call to mail() ie 

```
mail(valid@address.com, 'Test Subject', 'Test message')
```

Wrapping it in an 'if else' might shed some light too :D

---

### Post by lykwydchykyn on 2011-10-25
If sendmail is configured correctly, you should be able to send mail from the terminal, like so:
```

echo "test"|mail -s test myemail@myemail.yeah

```

That's the first place I'd start if php isn't sending mail.  If that mail comes through, your issue is with php or your code.

If it doesn't, your issue is with the sendmail configuration.

---

### Post by 1cookie on 2011-10-25
> **satanselbow said:**
> Does the timestamp on the SIGTERM match the time you send the mail? They may not be related as they were appearing in your logs previously... might be a dodgy extension? (incorrect version?)

Might be an idea to turn all php errors on as well to see if there is something else in the script not behaving as it should ;) 

Errors are ON. Nothing reported at runtime.

> 
Have you tried a vanilla call to mail() ie 

I modified my code to:

```

<?php
if( mail('myemail@yahoo.com', 'test subject', 'hello this is a test') ){

    echo 'Mail was sent';
} else {
    echo 'Couldn\'t send the mail';
}

```Run it, and it prints 'Mail was sent'.

I dont think there's anything wrong with the script/code.

---

### Post by 1cookie on 2011-10-25
> **lykwydchykyn said:**
> If sendmail is configured correctly, you should be able to send mail from the terminal, like so:
```

echo "test"|mail -s test myemail@myemail.yeah

```That's the first place I'd start if php isn't sending mail.  If that mail comes through, your issue is with php or your code.

If it doesn't, your issue is with the sendmail configuration.

I tried ```

andy@andy-R519-R719:~$ echo "test"|mail -s test myemail@yahoo.com
andy@andy-R519-R719:~$ echo "test"|mail -s test myemail@yahoo.com
andy@andy-R519-R719:~$ echo "test"|mail -s test myemail@yahoo.com


```at the shell. Still no mail in my inbox. All this leads me to thinking theres a problem with Sendmail. I'm going to have a Google for Sendmail configurations/set up issues. Do you know your way around Sendmail?

---

### Post by Bachstelze on 2011-10-25
If you are going to have to do manual configuration, you'll probably be better off using Postfix instead of Sendmail.

Mail can be tricky so more informatin about your environment would be helpful. Where is the machine located? At home or in a DC? If at home, behind a NAT? Static or dynamic IP?

---

### Post by lykwydchykyn on 2011-10-25
> **Bachstelze said:**
> If you are going to have to do manual configuration, you'll probably be better off using Postfix instead of Sendmail.


I'll second that; I always use postfix myself.  It's much easier to configure and sendmail is pretty dated from what I understand.

---

### Post by 1cookie on 2011-10-26
hi

A couple of things:

1. I'm still getting a notice in error.log

```

[Wed Oct 26 08:41:57 2011] [notice] Apache/2.2.20 (Ubuntu) PHP/5.3.6-13ubuntu3.2 with Suhosin-Patch configured -- resuming normal operations

```This momentarily causes Apache to report 'Unable to Find localhost'. Upon re-loading the page all my files/directories come back! It's just a bit of a niggle.


2. With the Sendmail/Postfix business. My email account is through web mail. Looking at this [https://help.ubuntu.com/8.04/serverguide/C/postfix.html](https://help.ubuntu.com/8.04/serverguide/C/postfix.html) tutorial on Postfix. I haven't got a 'Danny la ru' what my:

> 
 mail server hostname, and 192.168.0/24 with the actual network and class          range of your mail server.
is?? :) Well I could have a stab at the first one. I'm using *******@yahoo.com, so I guess something along the lines of yahoo.com but I can't be sure with their servers?

Am i over complicating things here?

:)

---

### Post by 1cookie on 2011-10-28
> **Bachstelze said:**
> 
Where is the machine located? At home or in a DC?

At home.



> 
 If at home, behind a NAT? Static or dynamic IP?
It's gonna be a dynamic IP me thinks. Virgin media broadband at a residential property.

---

### Post by jgvitella on 2012-09-17
Hi guys,
Did you manage to solve the issue? I am having exactly the same problem. I tried different suggestions from this thread, but still I do not get my localhost to send an email to an external email address.

Any help or update is welcome

/Thanks

---

### Post by pqwoerituytrueiwoq on 2012-09-17
i have used [this]("https://code.google.com/a/apache-extras.org/p/phpmailer/") successfully
i was using ubuntu 10.04 at the time
here is the php script i used to send the email
[https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/email.php](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/email.php)
i have used the mail function successfully but it took about 30min (or 10 min, i forget) to receive the email i was using verizon dsl at the time

---

