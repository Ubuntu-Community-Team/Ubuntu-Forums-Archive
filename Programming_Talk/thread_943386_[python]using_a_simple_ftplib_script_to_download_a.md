---
title: "[python]using a simple ftplib script to download a file"
date: 2008-10-10
forum: Programming Talk
---

### Post by Pyro.699 on 2008-10-10
Hello,

I have this script:

```

import ftplib

def download(ftp,directory,file):
    ftp.cwd(directory)
    f = open(file,"wb")
    ftp.retrbinary("RETR " + file,f.write)
    f.close()
    
ftp = ftplib.FTP("ftp.domain.com")
ftp.login("username", "password")

download(ftp, "/www/path/to/file/", "file.ext")

```

and i know that the ftp logs in successfully (copied from another successful script (used for uploading) but for some reason, the file is not created. There are no errors returned and everything seems to run smoothly, but **file.ext** never appears in the working directory

Thanks
~Cody Woolaver

---

### Post by ghostdog74 on 2008-10-10
turn on ftplib's set_debuglevel().

---

### Post by Pyro.699 on 2008-10-10
Sorry folks, i was doing this in eclipse (pydev) and was getting this error. After i just tried (for the heck of it) it in the terminal and everything worked smoothly.

Thanks
~Cody Woolaver

---

