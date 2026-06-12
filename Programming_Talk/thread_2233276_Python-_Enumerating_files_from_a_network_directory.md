---
title: "Python- Enumerating files from a network directory"
date: 2014-07-07
forum: Programming Talk
---

### Post by Nick_Reardon on 2014-07-07
I've been searching how to enumerate files from a network directory for a couple hours now with no luck. I need to be able to do this with Python for an application that I am working on. PLEASE HELP!

Methods tried so far-

import os
>>> print os.path.splitext

from os import listdir
>>> from os.path import isfile, join
>>> onlyfiles = [f for f in listdir("smb:///dw_fileserver/") if isfile(join("smb:///dw_fileserver/", f))]

os.walk("smb:///dw_fileserver/")

---

### Post by Nick_Reardon on 2014-07-07
I just found the smbclient but the documentation is so poor that it's useless at this point. If anyone can explain it to me a little better I'd be happy.

---

### Post by ofnuts on 2014-07-07
os.path is for files that are locally mounted. To talk to a Samba server directly you can try [this](https://pypi.python.org/pypi/pysmb).

---

