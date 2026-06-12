---
title: "[SOLVED] Apache logs"
date: 2008-07-30
forum: New to Ubuntu
---

### Post by ub007 on 2008-07-30
Hi,

I'm trying to load test my Apache web server with Http requests.How can I view the logs for these requests?Thanks in advance...cheers
David

---

### Post by gvartser on 2008-07-30
```
tail -f /var/log/apache2/access.log
```

/g

---

### Post by ub007 on 2008-07-30
thank you,that helps....can i extract the log to a file?

---

### Post by gvartser on 2008-07-30
the log is a file located in:
/var/log/apache2/access.log.

the syntax: "tail -f" is simply reading the file continuously.
But you can also do a "cat" or "more" on the file allowing you to browse the file.

But if you need to extract it to another file, just simply do a cat with a redirect.

_Example:_
```
cat /var/log/apache2/access.log > /tmp/my_apache_access_log_file.txt
```

/g

---

### Post by ub007 on 2008-07-30
thank you:guitar:

---

