---
title: "Python FTP issues"
date: 2012-12-08
forum: Programming Talk
---

### Post by 3v3rgr33n on 2012-12-08
Hi All

I've been playing around with PyQt lately and I wanted to use it and the module ftplib for something cool. I've been having issues with the ftplib module, I do not know why it's not working and google isn't helping

The simplest code for instance```
from ftplib import FTP
f = FTP("ftp://ftp.leg.uct.ac.za/pub/")
print(f.getwelcome())

``` throws the following error

```
  File "test.py", line 2, in <module>
    f = FTP("ftp://ftp.leg.uct.ac.za/pub/")
  File "/usr/lib/python3.2/ftplib.py", line 113, in __init__
    self.connect(host)
  File "/usr/lib/python3.2/ftplib.py", line 142, in connect
    self.sock = socket.create_connection((self.host, self.port), self.timeout)
  File "/usr/lib/python3.2/socket.py", line 386, in create_connection
    for res in getaddrinfo(host, port, 0, SOCK_STREAM):
socket.gaierror: [Errno -2] Name or service not known
```

What does this mean? Please help

Regards
3v3rgr33n

---

### Post by trent.josephsen on 2012-12-08
Don't you think ftp:// is a little redundant? I tried without it and was able to connect to another server.

---

### Post by 3v3rgr33n on 2012-12-10
Lol Thanx, guess I was just being stupid. I removed it and it worked.

---

