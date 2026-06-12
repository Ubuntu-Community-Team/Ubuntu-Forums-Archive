---
title: "PHP Send Mail Problem"
date: 2008-12-12
forum: Programming Talk
---

### Post by Black Mage on 2008-12-12
I am having a problem sending mail with PHP. I think my problem lies in the fact that my mail server is different from my web server. I am using the PHP-PEARL to send mail and I set my php.ini to this:

sendmail_path = /usr/sbin/sendmail -i -t

But could it be because the path is on the web server than it is preventing me from sending mail?

And there error I recieve is: unable to connect to smtp server [email]ddixon@my-lan.us[/email]:25

Thanks

---

### Post by mssever on 2008-12-12
It sounds like the SMTP server on the PHP machine is misconfigured. Try sending a test message and see if it gets through: ```
echo "Test message" | mail -s "test subject" your@email.address
```

---

