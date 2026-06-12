---
title: "Need Easy Mail Server"
date: 2008-09-06
forum: Programming Talk
---

### Post by SuperMike on 2008-09-06
Anyone doing programming and they installed a quick and dirty mail server to do testing against for SMTP and POP?

I need something that's super easy to get going here. I was using Hula, but I can't use it with Hardy Heron.

I don't want something that requires a lot of braincells. They're all sucked away into my programming right now.

---

### Post by SuperMike on 2008-09-06
On Hardy Heron:

```
$ sudo su
# apt-get update
# apt-get install mailx
# tail -f /var/spool/mail/www-data
```

The tail command will hold with a blinking cursor, so you can ignore that for a second and continue...

And from your PHP page, do something like:

[PHP]<?php

mail(
	'to@test.com',
	'Test Subject',
	'Test Body',
	"From: [email]from@test.com[/email]\r\nReply-To: [email]from@test.com[/email]\r\nX-Mailer: PHP/" . phpversion()
);


?>
MAIL SENT[/PHP]

Now, connect to your web server and run your PHP test page.

Then, flip back to your command prompt and look at the result.

---

### Post by SuperMike on 2008-09-06
Even better. You may not know this, but if your PHP mail() command sends to root@localhost, you can use Thunderbird to pick up the mail if you configure it for your own account @localhost  (such as mike@localhost). There's a problem, though, with the default /var/spool/mail config and you have to do this first:

$ sudo chmod 1777 /var/spool/mail

Now when your PHP page sends mail to root@localhost, you can pick it up in Thunderbird.

---

