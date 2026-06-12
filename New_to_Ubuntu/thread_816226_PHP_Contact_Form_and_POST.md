---
title: "PHP Contact Form and POST"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by cackles on 2008-06-02
Im hoping this isnt a daft question, probably is, but do I need to install and confugire Postfix in order for a PHP contact form to work on my server?

The contact form 'appears' to work but Im not getting mail in from it when I test it. I havent setup any sort of mail but was planning to go for Postfix anyway but if this is a deifferent problem then I'd rather fix it before moving on.

This is the Contact Form script I am using:

[http://www.free-php.net/detail/link-12.html](http://www.free-php.net/detail/link-12.html)

---

### Post by bilbo.san on 2008-06-02
Hey, this has no relation with Ubuntu... but perhaps I can help you with something. but you are going to have to give me more details and perhaps part of the coding.

---

### Post by cackles on 2008-06-02
All the code is in the download on the page the link above takes you to.

I need to know what Ubuntu server needs to make it work.

I have Apache and PHP working fine on it.

---

### Post by cackles on 2008-06-03
Well after hammering away for 15hrs at postfix I have it working with my dyndns account and it actually works fine.

The mail() function though for php to send out mail still seems to be broken.

Ive changed the part under [mail function]in php.ini to this:

```
sendmail_path = /usr/sbin/postfix -t -i
```

Ive also broke the server a few times as well.

I have tried using a simple way to test mail:

```
<? mail(" xxx@xxx","test message","This is a test"); ?>
``` 

And about 10 other scripts :/

I just cannot get mail() to work.

Ive also just commented out that stupid cron job from sendmail that I managed to invoke that was messaging jibberish every 20 mins.

Any help appreciated.

---

### Post by hyper_ch on 2008-06-03
did you have a look at the postfix logs what they say?

my php.ini does not have any mail thing attached:

```

cp:/backup/old# cat /etc/php5/apache2/php.ini | grep mail
; Define the anonymous ftp password (your email address)
[mail function]
;sendmail_from = me@example.com
; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
;sendmail_path =
; to the sendmail binary. These parameters will always replace the value of
; the 5th parameter to mail(), even in safe mode.
;mail.force_extra_parameters =
;   to other person via. email/irc/etc.
; mail(), ereg(), etc are overloaded by mb_send_mail(), mb_ereg(),
; 1: Overload mail() function

```

---

