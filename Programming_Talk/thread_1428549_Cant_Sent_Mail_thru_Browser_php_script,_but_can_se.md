---
title: "Cant Sent Mail thru Browser php script, but can send thru commandline"
date: 2010-03-12
forum: Programming Talk
---

### Post by karekanu on 2010-03-12
Hi Guys,

I had a test php script to send a mail.
Executing a script to a browser, doesnt sent the mail.

But in a command line, it does.

```
jon@desktop:/opt/lampp/bin$ ./php /opt/lampp/htdocs/tests/testmail.php
PHP Warning:  mail(1): failed to open stream: Permission denied in /opt/lampp/htdocs/tests/testmail.php on line 9

Warning: mail(1): failed to open stream: Permission denied in /opt/lampp/htdocs/tests/testmail.php on line 9
Mail sent <br/>jon@desktop:/opt/lampp/bin$ 
```

Even though the warning, it successfully send the email. I'm using msmtp with gmail for
relaying the mail.

Any idea whats wrong? I guess i need to set some permission to allow the Browser Group or nobody group to execute the mail script to a browser? Do i add a nobody group for the lamp binary files?

---

### Post by Hellkeepa on 2010-03-13
HELLo!

Can you post the script, so we can see what it does?

Happy codin'!

---

