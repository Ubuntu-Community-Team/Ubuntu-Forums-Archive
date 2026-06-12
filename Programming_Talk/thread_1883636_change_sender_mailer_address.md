---
title: "change sender mailer address"
date: 2011-11-19
forum: Programming Talk
---

### Post by shaunak1234 on 2011-11-19
hi,
I have installed postfix, mailx.
when i sent a command line email
```
echo test |mail -s "test mail sent to external" shaunak1234@gmail.com
```

I got the email from Shaunak Chandwadkar [email]shaun@wallpapers.no-ip.org[/email]

And when I sent it from php I got reply from 
www-data [email]www-data@wallpapers.no-ip.org[/email]

where can I change this www-data to webmaster or no-reply
:confused:

---

### Post by shaunak1234 on 2011-11-19
Okay I figured out a few things and now I receive emails from 
www-data [email]no-reply@wallpapers.no-ip.org[/email] 

Now I know www-data is a group on my server,
Can I modify this group name?

---

### Post by shaunak1234 on 2011-11-19
Thanks for not replying,
I did it.
open terminal and type in
```
sudo passwd www-data
```
change the password 
login as www-data and the password you entered
then open users and groups rename www-data to whatever you what
save changes
login back to your main account 
then try sending email and see the magic
______________________________________________________________________________________________
[Earn MOney from ubuntu]("http://www.gainmoneyfast.com/services/banner_rotator.php?a_aid=53951&a_bid=3787")

---

### Post by Bachstelze on 2011-11-19
Goodness no, that's *not* the way to do it! When you send an email with PHP's mail() function, you can change the From header; that's how you do it.

---

### Post by lisati on 2011-11-19
> **Bachstelze said:**
> Goodness no, that's *not* the way to do it! When you send an email with PHP's mail() function, you can change the From header; that's how you do it.

Agreed. www-data is a "special" user, tinkering with it can cause problems for web-based stuff you host.

---

### Post by shaunak1234 on 2011-11-20
Have You done this?
I am trying from days!
It doesn't work?
I have tried hundreds of combination for php mail() function didn't work for me!
And anyways you are not changing the original name of www-data group, It just changes the alias or just used the changed name instead of www-data in any email.
The basic name for the system "www-data" remains the same.
If you got any better idea tel me!:D:KS

---

### Post by Bachstelze on 2011-11-20
Documentation exists for a reason...

[http://us3.php.net/manual/en/function.mail.php](http://us3.php.net/manual/en/function.mail.php)

See example 2.

---

### Post by shaunak1234 on 2011-11-20
I tried that buddy!!!!:)

---

### Post by shaunak1234 on 2011-11-20
Even then I gave it a try!
It didn't work!

```
<?php
$to      = 'shaunak1234@gmail.com';
$subject = 'the subject';
$message = 'hello';
$headers = 'From: webmaster@wallpapers.no-ip.org' . "\r\n" .
    'Reply-To: webmaster@wallpapers.no-ip.org' . "\r\n" .
    'X-Mailer: PHP/' . phpversion();
    
mail($to, $subject, $message, $headers);
?>
```

Didn't got any mail

---

### Post by shaunak1234 on 2011-11-20
> **Bachstelze said:**
> Documentation exists for a reason...

[http://us3.php.net/manual/en/function.mail.php](http://us3.php.net/manual/en/function.mail.php)

See example 2.

So got any other suggestion?

---

### Post by lisati on 2011-11-20
Did you check your outgoing mail queue and gmail's junk folder?

---

### Post by shaunak1234 on 2011-11-20
> **lisati said:**
> Did you check your outgoing mail queue and gmail's junk folder?

Checked everything at gmail no email there,
How do i check the queue whats the command?

---

### Post by lisati on 2011-11-20
I normally use webmin to keep an eye on my email system. I believe the "mailq" command can show you what's in the outgoing mail queue.

---

### Post by shaunak1234 on 2011-11-20
```
shaun@Shaunak:~$ mailq
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
29828E098F      550 Sun Nov 20 05:02:07  www-data@wallpapers.no-ip.org
(host smtpin.mx.facebook.com[69.171.244.13] refused to talk to me: 554 5.7.1 POL-P1 http://www.spamhaus.org/query/bl?ip=59.95.28.77)
                                         shaunak1234@facebook.com


```
That's all i have in queue, and that was just a trial email for checking facebook mail service. It was generated from my mail script, not the one as stated above in example 2

---

### Post by shaunak1234 on 2011-11-20
NO suggestions?:guitar:

---

### Post by lisati on 2011-11-20
The "stuck" item might be a clue: your IP address appears to be on a couple of DNSBL blacklists. [http://blacklistalert.org](http://blacklistalert.org) is one of my favourite places to check which ones and why.

---

### Post by Bachstelze on 2011-11-20
There's a link in the error message mailq shows you. Go visit it.

---

