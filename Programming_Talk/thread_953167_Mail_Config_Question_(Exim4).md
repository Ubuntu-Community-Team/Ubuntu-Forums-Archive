---
title: "Mail Config Question (Exim4)"
date: 2008-10-19
forum: Programming Talk
---

### Post by SuperMike on 2008-10-19
As a web developer, I'm using Exim4 on Ubuntu to allow me to send mail from PHP, and then it sticks stuff in /var/mail. I have found I can use Unix Movemail in Thunderbird to pick up my mail. I use this as a debugging mechanism.

The problem is that www-data's mail goes into /var/mail, but Thunderbird won't let me open it up. The only way I can access www-data's mail is to do:

$ sudo cat /var/mail/www-data

Do you know a way to configure Exim4 such that www-data mail is automatically copied to /var/mail/supermike, or redirected to /var/mail/supermike, or somehow let my Thunderbird open www-data@localhost mail?

---

### Post by Mister.Vash on 2008-10-19
You might want a forwarded - that may be the easiest way to set it up.

Does the www-data have an associated home directoy?  Creating a .forward file in that folder and pupulating that file with the address should do it.

[http://www.exim.org/exim-html-4.40/doc/html/filter_toc.html](http://www.exim.org/exim-html-4.40/doc/html/filter_toc.html)

---

### Post by SuperMike on 2008-10-21
> **Mister.Vash said:**
> Does the www-data have an associated home directoy?  Creating a .forward file in that folder and pupulating that file with the address should do it.

Great, so I found I could create '/var/www/.forward' as:

# Exim filter
deliver supermike@localhost

And then chown the file as www-data.mail with:

$ sudo chown www-data.mail /var/www/.forward

And then bounce exim4:

$ sudo /etc/init.d/exim4 stop
$ sudo /etc/init.d/exim4 start

Okay, that worked. Now my Unix Movemail configured Thunderbird account can access that mail.

Okay, question. The mail is coming as the following, and I was wondering if I could just receive the email like normal:

Subject: Mail delivery failed: returning message to sender
Sender: Mail Delivery System
Message:

blah blah
Mailing to remote domains is not supported
blah blah

Is there any way to play with the .forward so that it routes all mail to supermike with no "mail deliver failed" message?

---

### Post by unutbu on 2008-10-21
Try removing the word 'deliver' from the .forward file:```


# Exim filter
deliver supermike@localhost
```
to
```

# Exim filter
supermike@localhost
```

If that doesn't work, please include more of the blah blah's :)
> 
Subject: Mail delivery failed: returning message to sender
Sender: Mail Delivery System
Message:

blah blah
Mailing to remote domains is not supported
blah blah

---

