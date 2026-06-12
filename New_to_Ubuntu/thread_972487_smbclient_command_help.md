---
title: "smbclient command help?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by garyed on 2008-11-05
I'm trying to find the code to copy multiple files to my Windos 98 computer.
I can access it through smbclient but am a little lost after that.
At the smb\> promptI can do:
```
 put frame1.html \\frames\frame1.html 
``` 
to copy a file from my Ubuntu machine to Win98 machine but if I do :
```
 put *.html \\frames\*.html 
```
I get an error that *.html does not exist.
Also I can only copy files from my Ubuntu home directory when I'm on the 98 machine at the smb\> prompt. I've looked for tutorials about command line in smbclient but haven't found any thing that's helped yet.
Any ideas?

---

### Post by brandoncolorado on 2008-11-05
> **garyed said:**
> I'm trying to find the code to copy multiple files to my Windos 98 computer.
I can access it through smbclient but am a little lost after that.
At the smb\> promptI can do:
```
 put frame1.html \\frames\frame1.html 
``` 
to copy a file from my Ubuntu machine to Win98 machine but if I do :
```
 put *.html \\frames\*.html 
```
I get an error that *.html does not exist.
Also I can only copy files from my Ubuntu home directory when I'm on the 98 machine at the smb\> prompt. I've looked for tutorials about command line in smbclient but haven't found any thing that's helped yet.
Any ideas?

This help?
[http://learnlinux.tsf.org.za/courses/build/net-admin/ch08s02.html](http://learnlinux.tsf.org.za/courses/build/net-admin/ch08s02.html)

---

### Post by garyed on 2008-11-05
Thanks,
I found that I needed to use mput & mget for multiple files.
I still have a good bit of learning to do with the command line in smbclient.
I found this helpful too:
[http://www.circa.ufl.edu/handouts/networks/ftp.html](http://www.circa.ufl.edu/handouts/networks/ftp.html)

---

