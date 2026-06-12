---
title: "PHP Sendmail"
date: 2007-07-05
forum: Programming Talk
---

### Post by md5hash on 2007-07-05
i cant use the mail function in PHP, how can i enable/configure it?

thanks,

---

### Post by scxtt on 2007-07-05
do you have "sendmail" (or better yet, postfix) installed on your box?

---

### Post by md5hash on 2007-07-05
i just installed sendmail but i cant send

---

### Post by scxtt on 2007-07-05
you should be a bit more specific about what you're actually doing ...

---

### Post by md5hash on 2007-07-05
i installed sendmail with this commands .. apt-get install sendmail

now i want to send a mail from a php script using the mail function.. but its not working.. how do i configure it

---

### Post by scxtt on 2007-07-05
i'd make sure you can send an email from your box 1st ... try: **mailx -s "this is a test" [email]valid_email@address.com[/email] < file_with_text.txt** and see if you get it in your inbox ... also, i think postfix is A LOT better than sendmail ... (install mailx if you need to ;))

---

### Post by md5hash on 2007-07-05
i tried mailx, it produces no error but im not receiving any email. whats wrong?

---

### Post by scxtt on 2007-07-05
is it running? **ps -ef | grep sendmail**

i'd switch to postfix myself ...

also, some mail accounts (gmail for example) are rejecting email from hosts it doesn't "know" ... i can't send emails from my box to my gmail account, which pisses me off ...

---

### Post by md5hash on 2007-07-05
i already removed sendmail... here is the result of **ps -ef | grep sendmail**


```
root      5673     1  0 04:40 ?        00:00:00 sendmail: MTA: accepting connections          
1000      8528  8193  1 19:21 tty3     00:00:00 grep sendmail
```

---

### Post by scxtt on 2007-07-05
you've removed sendmail?  was that after your "ps -ef"?  did you replace it w/ postfix (postfix should start on installation)?

---

### Post by md5hash on 2007-07-05
ok i re-installled sendmail.. and its auto start on boot..  whats next?

---

### Post by md5hash on 2007-07-05
from my phpinfo()

sendmail_from	no value	no value
sendmail_path	/usr/sbin/sendmail -t -i 	/usr/sbin/sendmail -t -i 

SMTP	localhost	localhost
smtp_port	25	25

---

### Post by scxtt on 2007-07-05
mine's the exact same way - i'm just using postfix ... but i do have a /usr/sbin/sendmail ... all i can say is use postfix, not sendmail - i've never had to config postfix (aside from a random alias.db sometimes) ...

---

### Post by md5hash on 2007-07-06
can i install postfix with sendmail still in my system?

---

### Post by md5hash on 2007-07-06
bump! anyone?

---

### Post by scxtt on 2007-07-06
you probably can, but really there's no need for sendmail - postfix is "a sendmail replacement" ...

---

### Post by md5hash on 2007-07-06
installing postfix removes the sendmail.. i have postfix now with default configuration.. whats next?

---

### Post by scxtt on 2007-07-06
well, i feel like i'm starting to sound like a broken record, but you should test to make sure you can get postfix to send an email to an account from your box [via mailx is what i do] ... i've tested the mail function in php before and it worked for me (used a form that gathered an email address and some text, i didn't have any problems w/ it) - i mean all that's left is the fact that maybe your mail function is messed up? ...
[php]<?php
// The message
$message = "Line 1\nLine 2\nLine 3";

// In case any of our lines are larger than 70 characters, we should use wordwrap()
$message = wordwrap($message, 70);

// Send
mail('caffinated@example.com', 'My Subject', $message);
?>[/php]i used this (edited for content) and ran it w/ **php email.php** - worked fine.

---

### Post by md5hash on 2007-07-06
im also using almost the same code to test if mail function is work... 

mail('alabarda@viva.com.oh', 'test sub', "content") or die("failed to send");

PHP script say the email was sent because  the die part of the script didnt showup.. 

i checked the logs in /var/log/mail.log alot of them says stat= Deferred: Connection refused by viva.com.ph

im starting to faint .... arggghh

---

### Post by Mr. C. on 2007-07-06
So the remote connection is refusing your mail server.  The server **is** attempting to send.

Look at and show output from the **mailq** command.

Show the exact log messages for more help.

This really isn't a programming issue - you're likely to get better help in the Servers and Security forum.

MrC

---

### Post by md5hash on 2007-07-06
mailq returns mail queue is empty

here is the content of the /var/log/mail.log

```

Jul  6 22:03:38 iportal postfix/master[12988]: daemon started -- version 2.3.8, configuration /etc/postfix
Jul  6 22:08:36 iportal postfix/pickup[12991]: E9F36A3A730: uid=33 from=<www-data>
Jul  6 22:08:36 iportal postfix/cleanup[12996]: E9F36A3A730: message-id=<20070706140836.E9F36A3A730@iportal.viva.com.ph>
Jul  6 22:08:37 iportal postfix/qmgr[12992]: E9F36A3A730: from=<www-data@viva.com.ph>, size=353, nrcpt=1 (queue active)
Jul  6 22:08:37 iportal postfix/local[12998]: E9F36A3A730: to=<alabarda@viva.com.ph>, relay=local, delay=0.26, delays=0.16/0.06/0/0.03, dsn=5.1.1, status=bounced (unknown user: "alabarda")
Jul  6 22:08:37 iportal postfix/cleanup[12996]: 1B648A3A72F: message-id=<20070706140837.1B648A3A72F@iportal.viva.com.ph>
Jul  6 22:08:37 iportal postfix/qmgr[12992]: 1B648A3A72F: from=<>, size=2079, nrcpt=1 (queue active)
Jul  6 22:08:37 iportal postfix/bounce[12999]: E9F36A3A730: sender non-delivery notification: 1B648A3A72F
Jul  6 22:08:37 iportal postfix/qmgr[12992]: E9F36A3A730: removed
Jul  6 22:08:37 iportal postfix/local[12998]: 1B648A3A72F: to=<www-data@viva.com.ph>, relay=local, delay=0.09, delays=0.01/0/0/0.08, dsn=2.0.0, status=sent (delivered to mailbox)
Jul  6 22:08:37 iportal postfix/qmgr[12992]: 1B648A3A72F: removed
Jul  6 22:09:11 iportal postfix/pickup[12991]: DF491A3A730: uid=33 from=<www-data>
Jul  6 22:09:11 iportal postfix/cleanup[12996]: DF491A3A730: message-id=<20070706140911.DF491A3A730@iportal.viva.com.ph>
Jul  6 22:09:11 iportal postfix/qmgr[12992]: DF491A3A730: from=<www-data@viva.com.ph>, size=353, nrcpt=1 (queue active)
Jul  6 22:09:11 iportal postfix/local[12998]: DF491A3A730: to=<alabarda@viva.com.ph>, relay=local, delay=0.08, delays=0.07/0/0/0, dsn=5.1.1, status=bounced (unknown user: "alabarda")
Jul  6 22:09:11 iportal postfix/cleanup[12996]: F0FF6A3A731: message-id=<20070706140911.F0FF6A3A731@iportal.viva.com.ph>
Jul  6 22:09:11 iportal postfix/bounce[12999]: DF491A3A730: sender non-delivery notification: F0FF6A3A731
Jul  6 22:09:11 iportal postfix/qmgr[12992]: DF491A3A730: removed
Jul  6 22:09:11 iportal postfix/qmgr[12992]: F0FF6A3A731: from=<>, size=2079, nrcpt=1 (queue active)
Jul  6 22:09:11 iportal postfix/local[12998]: F0FF6A3A731: to=<www-data@viva.com.ph>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Jul  6 22:09:12 iportal postfix/qmgr[12992]: F0FF6A3A731: removed
Jul  6 22:12:31 iportal postfix/pickup[12991]: 304E7A3A730: uid=33 from=<www-data>
Jul  6 22:12:31 iportal postfix/cleanup[13025]: 304E7A3A730: message-id=<20070706141231.304E7A3A730@iportal.viva.com.ph>
Jul  6 22:12:31 iportal postfix/qmgr[12992]: 304E7A3A730: from=<www-data@viva.com.ph>, size=353, nrcpt=1 (queue active)
Jul  6 22:12:31 iportal postfix/local[13027]: 304E7A3A730: to=<alabarda@viva.com.ph>, relay=local, delay=0.12, delays=0.08/0.02/0/0.02, dsn=5.1.1, status=bounced (unknown user: "alabarda")
Jul  6 22:12:31 iportal postfix/cleanup[13025]: 4930DA3A72F: message-id=<20070706141231.4930DA3A72F@iportal.viva.com.ph>
Jul  6 22:12:31 iportal postfix/qmgr[12992]: 4930DA3A72F: from=<>, size=2079, nrcpt=1 (queue active)
Jul  6 22:12:31 iportal postfix/bounce[13028]: 304E7A3A730: sender non-delivery notification: 4930DA3A72F
Jul  6 22:12:31 iportal postfix/qmgr[12992]: 304E7A3A730: removed
Jul  6 22:12:31 iportal postfix/local[13029]: 4930DA3A72F: to=<www-data@viva.com.ph>, relay=local, delay=0.03, delays=0.01/0.02/0/0.01, dsn=2.0.0, status=sent (delivered to mailbox)
Jul  6 22:12:31 iportal postfix/qmgr[12992]: 4930DA3A72F: removed
Jul  6 22:19:51 iportal postfix[13033]: error: to submit mail, use the Postfix sendmail command
Jul  6 22:19:51 iportal postfix[13033]: fatal: the postfix command is reserved for the superuser
Jul  6 22:21:59 iportal postfix[13066]: fatal: usage: postfix [-c config_dir] [-Dv] command
Jul  6 22:34:18 iportal postfix/sendmail[13078]: fatal: Recipient addresses must be specified on the command line or via the -t option
Jul  6 22:56:43 iportal postfix/pickup[12991]: 56341A3A730: uid=0 from=<root>
Jul  6 22:56:43 iportal postfix/cleanup[13160]: 56341A3A730: message-id=<20070706145643.56341A3A730@iportal.viva.com.ph>
Jul  6 22:56:43 iportal postfix/qmgr[12992]: 56341A3A730: from=<root@viva.com.ph>, size=301, nrcpt=1 (queue active)
Jul  6 22:56:43 iportal postfix/local[13162]: 56341A3A730: to=<alabarda@viva.com.ph>, relay=local, delay=0.12, delays=0.07/0.02/0/0.02, dsn=5.1.1, status=bounced (unknown user: "alabarda")
Jul  6 22:56:43 iportal postfix/cleanup[13160]: 6E04BA3A72F: message-id=<20070706145643.6E04BA3A72F@iportal.viva.com.ph>
Jul  6 22:56:43 iportal postfix/bounce[13163]: 56341A3A730: sender non-delivery notification: 6E04BA3A72F
Jul  6 22:56:43 iportal postfix/qmgr[12992]: 56341A3A730: removed
Jul  6 22:56:43 iportal postfix/qmgr[12992]: 6E04BA3A72F: from=<>, size=2019, nrcpt=1 (queue active)
Jul  6 22:56:43 iportal postfix/local[13162]: 6E04BA3A72F: to=<administrator@viva.com.ph>, orig_to=<root@viva.com.ph>, relay=local, delay=0.09, delays=0.01/0/0/0.08, dsn=2.0.0, status=sent (delivered to mailbox)
Jul  6 22:56:43 iportal postfix/qmgr[12992]: 6E04BA3A72F: removed
Jul  6 22:59:13 iportal postfix/master[12988]: terminating on signal 15
Jul  6 23:00:24 iportal postfix/master[3834]: daemon started -- version 2.3.8, configuration /etc/postfix
Jul  6 23:19:06 iportal postfix/sendmail[4035]: fatal: Recipient addresses must be specified on the command line or via the -t option

```

---

### Post by Mr. C. on 2007-07-06
Earlier you indicated you were trying to send to "alabarda@viva.com.ph".  This log entry shows that postfix has received your email from the system (php via apache, as user www-data ):

> Jul  6 22:12:31 iportal postfix/pickup[12991]: 304E7A3A730: uid=33 from=<www-data>

These shows the message is queued for delivery:

> Jul  6 22:12:31 iportal postfix/cleanup[13025]: 304E7A3A730: message-id=<20070706141231.304E7A3A730@iportal.viva.com.ph>
Jul  6 22:12:31 iportal postfix/qmgr[12992]: 304E7A3A730: from=<www-data@viva.com.ph>, size=353, nrcpt=1 (queue active)


And this message shows that user **alabarda** is an unknown local user:

> Jul  6 22:12:31 iportal postfix/local[13027]: 304E7A3A730: to=<alabarda@viva.com.ph>, relay=local, delay=0.12, delays=0.08/0.02/0/0.02, dsn=5.1.1, status=bounced (unknown user: "alabarda")

Is viva.com.ph your domain ?  if so, do you have a user alabarda ?

MrC

---

### Post by scxtt on 2007-07-06
i had a feeling this was the case (well. that the messages were being rejected on the receiver end, for some reason) ... i fought w/ this stuff too, only i had initial success - then gmail decided i was spamming myself - but it was working for a month or two before gmail started rejecting them :( ...

---

### Post by md5hash on 2007-07-06
im sorry but new here..

yes viva.com.ph is our domain and i use alabarda as login to my email...

heres what im trying to do..

im setting up a linux server for our intranet portals, the use of this email function for the user to send email from my php scripts.. i have the portal already running smoothly but in windows 2003 server..

---

### Post by Mr. C. on 2007-07-06
That's fine, but you have to have valid recipients to deliver mail,or your delivery any unmatched recipients to a listed recipient.

So where do you want the email to go ?  Local mailboxes ?  Forwarded to other email addresses?  Virtual mailboxes ?  Postfix needs to know what to do with it, and currently you have it configured accept email for your domain.

MrC

---

### Post by scxtt on 2007-07-06
i used the to do the same type of thing - have my boxes send emails of config files to an email server on Windows Server 2003 - worked w/o a hitch - maybe you have a config on the windows side that isn't working?

it is sending, but where you're sending it is rejecting the emails ...

---

### Post by Mr. C. on 2007-07-06
No, the relay is "local", which means the system is trying to send to users in the machines password or aliases file.

MrC

---

### Post by md5hash on 2007-07-06
> **Mr. C. said:**
> That's fine, but you have to have valid recipients to deliver mail,or your delivery any unmatched recipients to a listed recipient.

So where do you want the email to go ?  Local mailboxes ?  Forwarded to other email addresses?  Virtual mailboxes ?  Postfix needs to know what to do with it, and currently you have it configured accept email for your domain.

MrC

**i think theyre valid, im sending to my own email addresses

**from the php script i want to send it to their email address or any email address specified in the script.

do you guys have instant messengers, so i can ask.. i prefer ym
heres my userid **vbnullchar**

thanks

---

### Post by Mr. C. on 2007-07-06
Yes, some of your users are getting their email.  But postfix is telling us user "alabarda" does not exist in the tables used by postfix for local mail delivery.

relay=**local**, delay=0.12, delays=0.08/0.02/0/0.02, dsn=5.1.1, status=bounced (**unknown user: "alabarda"**

Can you get an up to date description what the prolems are you're facing ?

MrC

---

### Post by scxtt on 2007-07-06
is it possible this is coming from the way postfix was configured during install? - i think i choose "internet site" every time ... maybe md5hash didn't do this?

**sudo dpkg-reconfigure postfix**

---

### Post by md5hash on 2007-07-06
> **Mr. C. said:**
> Yes, some of your users are getting their email.  But postfix is telling us user "alabarda" does not exist in the tables used by postfix for local mail delivery.

relay=**local**, delay=0.12, delays=0.08/0.02/0/0.02, dsn=5.1.1, status=bounced (**unknown user: "alabarda"**

Can you get an up to date description what the prolems are you're facing ?

MrC

> **Mr. C. said:**
> Yes, some of your users are getting their email. But postfix is telling us user "alabarda" does not exist in the tables used by postfix for local mail delivery. i dont have any users, the only user stored in my linux server is administrator

> **Mr. C. said:**
> Can you get an up to date description what the prolems are you're facing ? the server im using is not intended to be a email server but a simple webserver that can send email to other employees.. and thats the problem i cant send emails

---

### Post by Mr. C. on 2007-07-06
You're asking us to guess too many details that are required to be known to configure a mail server or mail relay.

If you want all mail from your local ubuntu box to foward email to another company server, you need to configure it as a relayhost for your companies domain.  And your machine cannot then be configured to have postfix's mydestination listing your companies domain.

Please, save us all some time,and describe as precisely as you can what you are trying to accomplish, including the systems you have inhouse, or servers you need to forward to, etc.

MrC

---

### Post by md5hash on 2007-07-06
ok this is really hard for me.. 

we have 3 servers here a proxy,email, local web server. 

the web server (linux), this is where all the local intranet sites is located.. there is a script here that has a form that lets you send emails to the outside world.. using a windows server i dont have much problem b'cuz will just confgure my php.ini and set sendmail_from=alabarda@viva.com.ph and SMTP=130.10.1.8 (this is the ip of our email server) thats it, i can now use php mail function.

---

### Post by scxtt on 2007-07-06
do you remember what you selected when you installed postfix?  i'd run **sudo dpkg-reconfigure postfix** and make sure you do "internet site" or whatever is closest ...

---

### Post by Mr. C. on 2007-07-06
Ok, fine.  You want your server to be a general outbound SMTP server for your webscript.  Thats easiy.

I saw nothing in your log file that indicated you tried to send anything outbound to another domain.  If that is failing, show the log messages for that failure.

MrC

---

### Post by md5hash on 2007-07-06
heres the last failed log

```
Jul  7 01:33:30 iportal postfix/pickup[4075]: D94DDA3A730: uid=33 from=<www-data>
Jul  7 01:33:30 iportal postfix/cleanup[4137]: D94DDA3A730: message-id=<20070706173330.D94DDA3A730@iportal.viva.com.ph>
Jul  7 01:33:30 iportal postfix/qmgr[3845]: D94DDA3A730: from=<www-data@viva.com.ph>, size=353, nrcpt=1 (queue active)
Jul  7 01:33:30 iportal postfix/local[4139]: D94DDA3A730: to=<alabarda@viva.com.ph>, relay=local, delay=0.12, delays=0.08/0.02/0/0.02, dsn=5.1.1, status=bounced (unknown user: "alabarda")
Jul  7 01:33:30 iportal postfix/cleanup[4137]: F24E3A3A72F: message-id=<20070706173330.F24E3A3A72F@iportal.viva.com.ph>
Jul  7 01:33:30 iportal postfix/qmgr[3845]: F24E3A3A72F: from=<>, size=2079, nrcpt=1 (queue active)
Jul  7 01:33:31 iportal postfix/local[4139]: F24E3A3A72F: to=<www-data@viva.com.ph>, relay=local, delay=0.01, delays=0.01/0/0/0, dsn=2.0.0, status=sent (delivered to mailbox)
Jul  7 01:33:31 iportal postfix/qmgr[3845]: F24E3A3A72F: removed
Jul  7 01:33:31 iportal postfix/bounce[4140]: D94DDA3A730: sender non-delivery notification: F24E3A3A72F
Jul  7 01:33:31 iportal postfix/qmgr[3845]: D94DDA3A730: removed
```

---

### Post by md5hash on 2007-07-06
> **scxtt said:**
> do you remember what you selected when you installed postfix?  i'd run **sudo dpkg-reconfigure postfix** and make sure you do "internet site" or whatever is closest ...

i selected **internet site**

---

### Post by Mr. C. on 2007-07-06
There is nothing in your log messages that indicate an attempt to "**send emails to the outside world**.  You are still addressing mail for the local machine itself :

```
... to=<alabarda@viva.com.ph> ...
```

and the only reason this fails is because there is **no such user** alabarda.

MrC

---

### Post by md5hash on 2007-07-10
i installed ssmtp and removed postfix from the server it starts sending emails, im still confused but i think its fine.. thanks guys

---

### Post by Mr. C. on 2007-07-10
Be careful with ssmtp - it does not manage a queue, and mail may be lost if the connection is not made.  If you care about your email, you need a real MTA.

MrC

---

### Post by md5hash on 2007-07-10
i have no choice but to use it temporarily until i can get postfix to work...

---

### Post by chobong on 2010-01-27
Hi All,

Im using sendmail on my server.
When I send an email with command line on Ubuntu server, it's working fine. 
But when I use sendmail with php, default it takes root@mydomain for sender(not my sender's email which i typed in) and I cant receive mail.

Please help me !!!
Thanks all

---

### Post by lisati on 2010-01-27
> **chobong said:**
> Hi All,

Im using sendmail on my server.
When I send an email with command line on Ubuntu server, it's working fine. 
But when I use sendmail with php, default it takes root@mydomain for sender(not my sender's email which i typed in) and I cant receive mail.

Please help me !!!
Thanks all

Like it says earlier in this old thread, sometimes it's better to use postfix.

---

### Post by chobong on 2010-01-27
I tested with the php file as follows

<?php

$Name = "Sarah Pham"; //senders name
$email = "sarah.pham@abc.com"; //senders e-mail adress
$recipient = "kelly.do@abc.com"; //recipient
$mail_body = "The text for the mail..."; //mail body
$subject = "Subject for reviever"; //subject
$header = "From: ". $Name . " <" . $email . ">\r\n"; //optional headerfields

ini_set('sendmail_from', [EMAIL="%27tony.phan@mbizglobal.vn"]'sarah.pham@abc.com[/EMAIL]'); /
mail($recipient, $subject, $mail_body, $header); //mail command 
echo $header;
?>

This is the log file 
Jan 27 18:11:51 vn-local sm-mta[6085]: o0RABp3N006085: from=<root@vn-local.com>, size=344, class=0, nrcpts=1, msgid=<201001271011.o0RABp1g006084@vn-local.com>, proto=ESMTP, daemon=MSP-v4, relay=localhost [127.0.0.1]
Jan 27 18:11:51 vn-local sendmail[6084]: o0RABp1g006084: to=kelly.do@abc.com, ctladdr=root (0/0), delay=00:00:00, xdelay=00:00:00, mailer=relay, pri=30127, relay=[127.0.0.1] [127.0.0.1], dsn=2.0.0, stat=Sent (o0RABp3N006085 Message accepted for delivery)

Although stat=Sent, but I can't received the email. Sender's email is [email]root@vn-local.com[/email], not [email]sarah.pham@abc.com[/email] .

Please help me!! :(

---

### Post by Hellkeepa on 2010-01-27
HELLo!

Check the mail configuration settings in "php.ini".
Also, the mail headers should be terminated by a newline alone, not a carriage return + newline. (*Glares at MS*)

Happy codin'!

---

### Post by chobong on 2010-01-27
Thanks HellKeepa!

Here is the mail configuration in 'php.ini'

[mail function]
SMTP = localhost
smtp_port = 25

I tried to with 'sendmail_path'(/usr/sbin/sendmail) and 'sendmail_from', but it was not work :(

Could you pls let me know cause of this error? I don't understand about this problem((.
Thank you very much.

---

### Post by Hellkeepa on 2010-01-28
HELLo!

Seems to be a sendmail issue, I recommend having a look at these results:
[http://www.google.no/search?client=opera&rls=en-GB&q=sendmail+changing+address&sourceid=opera&ie=utf-8&oe=utf-8](http://www.google.no/search?client=opera&rls=en-GB&q=sendmail+changing+address&sourceid=opera&ie=utf-8&oe=utf-8)

Happy codin'!

---

