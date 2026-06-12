---
title: "bash, ftp read stdin"
date: 2010-08-19
forum: Programming Talk
---

### Post by genjix on 2010-08-19
> 
$ ftp
ftp> open ftp.genjix.com
Connected to ftp.genjix.com.
220 ProFTPD 1.2.9 Server (ProFTPD) [1.1.62]
Name (ftp.genjix.com:genjix): blaablaa
331 Password required for blaablaa.
Password:
230 User blaablaa logged in.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
200 PORT command successful
150 Opening ASCII mode data connection for file list
drwxr-xr-x   2 1001706  888            22 Oct  5  2009 genjix.com
drwxr-xr-x   7 1001706  888          4096 Aug 14 16:57 genjix.net
226 Transfer complete.
ftp> quit
221 Goodbye.


Wanting to script this I did something like:

> 
#!/bin/sh
ftp << EOD
open ftp.genjix.com
blaablaa
secretpass
dir
quit
EOD


This did not work. I tried open ftp.genjix.com\nuser blaa pass and passive\nftp.genjix.com... none of these worked. Any suggestions?

Thanks

---

### Post by ghostdog74 on 2010-08-19
you need the -n option. check the ftp man page. Also, change your shebang to #!/bin/bash if needed

---

### Post by jobix on 2010-08-19
It might be helpful if you could post the exact error messages.

---

### Post by genjix on 2010-08-19
-n did the trick. thanks

---

