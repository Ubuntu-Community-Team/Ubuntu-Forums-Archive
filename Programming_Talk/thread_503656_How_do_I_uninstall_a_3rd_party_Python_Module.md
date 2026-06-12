---
title: "How do I uninstall a 3rd party Python Module"
date: 2007-07-18
forum: Programming Talk
---

### Post by Andrew1234 on 2007-07-18
How can I uninstall a 3rd party python module, as I have installed ftputil and it does not seem to be able to see FTPHost, as I get this error:
[quote]
import ftputil


# download some files from the login directory
host = ftputil.FTPHost('ftp.domain.com', 'user', 'password')
names = host.listdir(host.curdir)
for name in names:
	if host.path.isfile(name):
		host.download(name, name, 'b')  # remote, local, binary mode
>>> 
Traceback (most recent call last):
  File "/home/andrew/Desktop/ftputil.py", line 1, in <module>
    import ftputil
  File "/home/andrew/Desktop/ftputil.py", line 5, in <module>
    host = ftputil.FTPHost('ftp.domain.com', 'user', 'password')
AttributeError: 'module' object has no attribute 'FTPHost'
>>> [/qoute]
I have search the web but cannot find any answers? Thanks

---

### Post by pmasiar on 2007-07-18
You don't need to unistall it - just ignore it and don't import it. Did you looked at ftplib module, included as standard? Something is missing?

BTW to show code, use the [ code ] tag, not  [ quote ] tag.

---

