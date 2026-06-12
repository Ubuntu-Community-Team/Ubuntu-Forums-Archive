---
title: "Using pyGTK to manage FTP transfers"
date: 2006-08-04
forum: Programming Talk
---

### Post by OneSeventeen on 2006-08-04
I'm working on an app where I want to be able to basically create a small/limited FTP client using pyGTK.

Since I have only been using python for a few days, I'm not quite sure how to connect to an FTP server and how to get/put files and how to get a listing of files...

Any tips?

I'd prefer something cross-platform, but wouldn't mind doing something linux-specific if it makes things easier while I learn.

---

### Post by gunderwood on 2006-08-04
Check here to start it's the reference pages for the python ftp library.

[http://docs.python.org/lib/module-ftplib.html](http://docs.python.org/lib/module-ftplib.html)

Cheers 
Greg

---

### Post by dabear on 2006-08-04
> **OneSeventeen said:**
> I'm working on an app where I want to be able to basically create a small/limited FTP client using pyGTK.

Since I have only been using python for a few days, I'm not quite sure how to connect to an FTP server and how to get/put files and how to get a listing of files...

Any tips?

I'd prefer something cross-platform, but wouldn't mind doing something linux-specific if it makes things easier while I learn.

```

sudo aptitude install ipython
ipython

```
and then in the ipython console:
```

import ftplib
help ftplib

```

example provided by help in the ipython console:
> 
  >>> from ftplib import FTP
    >>> ftp = FTP('ftp.python.org') # connect to host, default port
    >>> ftp.login() # default, i.e.: user anonymous, passwd anonymous@
    '230 Guest login ok, access restrictions apply.'
    >>> ftp.retrlines('LIST') # list directory contents
    total 9
    drwxr-xr-x   8 root     wheel        1024 Jan  3  1994 .
    drwxr-xr-x   8 root     wheel        1024 Jan  3  1994 ..
    drwxr-xr-x   2 root     wheel        1024 Jan  3  1994 bin
    drwxr-xr-x   2 root     wheel        1024 Jan  3  1994 etc
    d-wxrwxr-x   2 ftp      wheel        1024 Sep  5 13:43 incoming
    drwxr-xr-x   2 root     wheel        1024 Nov 17  1993 lib
    drwxr-xr-x   6 1094     wheel        1024 Sep 13 19:07 pub
    drwxr-xr-x   3 root     wheel        1024 Jan  3  1994 usr
    -rw-r--r--   1 root     root          312 Aug  1  1994 welcome.msg
    '226 Transfer complete.'
    >>> ftp.quit()
    '221 Goodbye.'
    >>>


---

### Post by Daverz on 2006-08-04
You might also want to take a look at twisted.

---

### Post by OneSeventeen on 2006-08-08
Thanks for the tips... I just recently discovered the manual, and it's pretty helpful!  I'll try out ipython for reading documentation, but are there any GUI interfaces to the python documentation? (Perhaps some that are printable?)

And, I'd just like to point out the irony that without any decimal markers, the section for the ftplib in the python manual is "117" :D

Thanks again!  I'll post back here when I get some working samples!

---

### Post by Daverz on 2006-08-08
> **OneSeventeen said:**
> but are there any GUI interfaces to the python documentation? (Perhaps some that are printable?)


devhelp.  Packages are devhelp and python-doc.  There's also a python doc sidebar for firefox.

---

