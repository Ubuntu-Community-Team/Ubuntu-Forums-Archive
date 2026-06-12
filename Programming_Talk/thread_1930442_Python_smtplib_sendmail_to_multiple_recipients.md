---
title: "Python: smtplib sendmail to multiple recipients?"
date: 2012-02-23
forum: Programming Talk
---

### Post by donsy on 2012-02-23
I'm trying to send an e-mail to multiple recipients using Python's smtplib library. The recipients are in a list as required in the Python 3.1.3 documentation for ```
SMTP.sendmail(*from_addr*, *to_addrs*, *msg*[, *mail_options*, *rcpt_options*])
```, but I consistently get the following error:```

Traceback (most recent call last):
  File "./sendEmail.py", line 41, in <module>
    s.sendmail(sender, recipients, msg.as_string())
  File "/usr/lib/python3.2/email/message.py", line 168, in as_string
    g.flatten(self, unixfrom=unixfrom)
  File "/usr/lib/python3.2/email/generator.py", line 91, in flatten
    self._write(msg)
  File "/usr/lib/python3.2/email/generator.py", line 144, in _write
    self._write_headers(msg)
  File "/usr/lib/python3.2/email/generator.py", line 178, in _write_headers
    header_name=h)
  File "/usr/lib/python3.2/email/header.py", line 205, in __init__
    self.append(s, charset, errors)
  File "/usr/lib/python3.2/email/header.py", line 281, in append
    s = s.decode(input_charset, errors)
AttributeError: 'list' object has no attribute 'decode'


```

---

