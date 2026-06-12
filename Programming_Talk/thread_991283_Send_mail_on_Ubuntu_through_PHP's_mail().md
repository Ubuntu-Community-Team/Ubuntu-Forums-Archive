---
title: "Send mail on Ubuntu through PHP's mail()"
date: 2008-11-23
forum: Programming Talk
---

### Post by nbakewell on 2008-11-23
Hey all,

I'm trying to get my LAMP Server to be able to use PHP's mail() function to successfully send emails from localhost, however I don't really know how to do this.  I've been reading through tutorials on how to make Ubuntu a mail server (there currently is one in the Tips & Tutorials forum) but I don't think I need to do quite that match.  I just need someway so that when I invoke mail() it will properly send my message - whether that is achieved by creating a mini mail server on Ubuntu and setting up POP3 or IMAP or something or somehow just configuring PHP to connect to my personal website's email server (this seems like it would be the easiest and most efficient way to do this?)

Any help is much appreciated - thanks!

---

### Post by drubin on 2008-11-23
Firstly have you set up the lamp server. ie is php running? if not see my sig
So you have any form of mail server set up?

---

### Post by nbakewell on 2008-11-23
Yes, PHP/Apache/MySQL is running.  I don't currently have any mail server set up.

---

### Post by drubin on 2008-11-23
[http://www.cyberciti.biz/tips/howto-php-send-email-via-smtp-authentication.html](http://www.cyberciti.biz/tips/howto-php-send-email-via-smtp-authentication.html)

This might also help (but is a little outdated)
[http://ubuntuforums.com/showthread.php?t=34786](http://ubuntuforums.com/showthread.php?t=34786)

---

