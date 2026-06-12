---
title: "Mail System"
date: 2011-12-27
forum: Programming Talk
---

### Post by barney_parker on 2011-12-27
Hi,

Not sure if this is the best section of the forums, please let me know if i need to move it elsewhere!

I am developing a web app which needs to be able to send out emails.

The App is built in PHP and is functioning fine.  I am able to send emails, there are a variety of methods, but in particular, all the PHP libraries seem to be geared to sending single emails.

I am sending emails via a smart-host.

This normally wouldn't be an issue, however each email can take anywhere from 2 to 15 seconds to send!

In each instance, the whole process of opening the connection, authenticating, transferring the mail, then closing the connection happen, which seems both wasteful and slow!

The problem is there are times where a pretty large number of mails need to be sent, sometimes on the order of several hundred.  This can take many minutes, which is far less than ideal!

So I am wondering if anyone has any suggestions?

The options as i see it (and i may well be missing something!) are:
1) a better method of sending mails via PHP
    - Send multiple mails on a single connect/auth cycle

2) use a local relay
    - only allow sending from localhost, but no auth to speed up connection times.

Either of these suggestions could work (possibly???)

I've done a fair bit of googling, and either there's not alot about, or i'm just googling for the wrong thing!

Any comments or suggestions would be welcomed, anything to get me heading in the right direction would be great!!!

---

### Post by Bachstelze on 2011-12-27
1) I'm not totally sure (the protocol is very complicated), but IIRC the SMTP protocol does not allow sending multiple emails in a single connection. What you can do is send the same email to a lot of people (just put all the addresses in the To field).

2) This seems to be the easiest option. Just install Postfix or Sendmail, and the default settings should be fine (assuming you don't have problems with your ISP or something else that would prevent the server to operate correctly).

---

### Post by barney_parker on 2011-12-27
Thanks for the reply.

1) It would seem that SMTP is able to send multiple emails in a single stream, and the Zend_Mail library can handle it.  Unfortunately i'm not using the zend framework.  I'm hoping i can find something similar...

2) Can Sendmail be configured to itself use a smarthost?  

I'm using my ISP as a smarthost, so currently my App opens an SMTP connection to my ISP.  I am hoping it would be faster if it were to a local server which didn't need authentication.

It appears that it's the authentication that is the slowest portion, so option (1) looks like the best one, but option (2) could also work...

---

### Post by Bachstelze on 2011-12-27
Hmm, have a look at [http://pear.php.net/package/Mail](http://pear.php.net/package/Mail)

If you use postfix with a smarthost, you will probably have the same problem.

---

### Post by barney_parker on 2011-12-29
The PEAR mail system only appears to allow single mail sending, i.e. a full connect, send, disconnect cycle for every mail

I came across xPertMailer, which is pretty damned good!

It allows you to use a MAIL object, but also an SMTP object.  This let me send out multiple emails, and I just needed to issue a Rset command between each to ensure the mail server was 100% aware of the break between mails.  

I have however hit another issue....  ISP bulk sending limitations....

Since i'm using my ISP as a smart host, it would seem that sending too many emails looks like an attempt at spamming, so they block SMTP logins for a while, essentially rate limiting.

So now i'm looking at external vendors, for example postmark, which although costs, gets over the issue of inadvertant spam detecting!

---

