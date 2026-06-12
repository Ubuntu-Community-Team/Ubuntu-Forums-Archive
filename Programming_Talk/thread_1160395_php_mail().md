---
title: "php mail()"
date: 2009-05-15
forum: Programming Talk
---

### Post by mvalviar on 2009-05-15
Hi,

I'm playing on a live server and I can't get the mail function to work I have ```

<?php
ini_set('sendmail_from', 'no-reply@myserver.com');
if (mail('me@mygmail.com', 'mail from php mail()', 'Hello', 'From: No Reply <no-reply@myserver.com>')) echo "OK";

```

I see the "OK" but I don't receive the mail? I there something wrong with what I'm doing?

I read something like "Keep in mind that just because the email was accepted for delivery, it does NOT mean the email is actually sent...". Does this apply here?

---

### Post by simeon87 on 2009-05-15
Your hosting company may have disabled it to prevent their server from being used as a spamming tool.

---

### Post by mvalviar on 2009-05-15
So there is nothing wrong with may code, is there? Its just that the mail thingy has been disabled.

---

### Post by simeon87 on 2009-05-15
I have no experience with mailing through PHP but the code looks syntactically valid PHP and the given arguments match those in the documentation, so I'd guess so.

---

