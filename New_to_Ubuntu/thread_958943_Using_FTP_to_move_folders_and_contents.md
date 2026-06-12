---
title: "Using FTP to move folders and contents"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by protargol on 2008-10-25
How can you use ftp in the command line to move folders and their contents, ie recursively.

When I run:
> sftp username@adress
cd directory/thatIwant/ 
put dir_that_I_want_to_transfer/. .

It gives me the error:
> skipping non-regular file dir_that_I_want_to_transfer/.


Any ideas?

---

### Post by kilroy423 on 2008-10-26
You could create a directory and then change to that directory and use put *

---

### Post by ciscosurfer on 2008-10-26
A few methods come to mind:  rsync, wget, scp, lftp, ncftp, and ftp (the last three all using put and get, as kilroy423 stated), you could tar the entire contents of each directory and send like that, etc., etc.  All of those have recursive switches of some kind you can use, most in the form of dash-r. The wget utility has recursive and mirror switches that I find useful. If you like the gui then gftp is nice; if you like using a browser, then FireFTP works well```
man rsync
man wget
man scp
man lftp
man ncftp

```

---

### Post by protargol on 2008-10-27
> **ciscosurfer said:**
> A few methods come to mind:  rsync, wget, scp, lftp, ncftp, and ftp (the last three all using put and get, as kilroy423 stated), you could tar the entire contents of each directory and send like that, etc., etc.  All of those have recursive switches of some kind you can use, most in the form of dash-r. The wget utility has recursive and mirror switches that I find useful. If you like the gui then gftp is nice; if you like using a browser, then FireFTP works well```
man rsync
man wget
man scp
man lftp
man ncftp

```

Yeah, I was using scp, but it was a very large amount of data in a large tree of folders that was behind a firewall that made it tricky to use wget and I just thought ftp would be faster.  I just didn't want to manually or create a script to reproduce the tree, but just hoped there was a recursive method.  Thanks for the advice though.

---

