---
title: "In Python how do I use ftplib to upload a file to server"
date: 2009-09-27
forum: Programming Talk
---

### Post by kn100 on 2009-09-27
def upload():
    ftpserver = 'ftp.randomserver.com'
    username = 'foo'
    password = 'bar' 
    ftp = ftplib.FTP(ftpserver)
    ftp.login(username, password)
    #here i want to upload a file called file.html, how do I do this
upload()


I can log in fine, but can not for the life of me figure out how to upload a file to the FTP server. Any help is greatly appreciated!

---

### Post by Can+~ on 2009-09-27
[PHP]ftp.storlines("STOR %s" % filename, open(filename))[/PHP]

---

