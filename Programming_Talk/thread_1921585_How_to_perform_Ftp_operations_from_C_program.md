---
title: "How to perform Ftp operations from C program"
date: 2012-02-07
forum: Programming Talk
---

### Post by srinidhi.kv on 2012-02-07
Hello All,
           I am writing a C program where I would like to connect to a ftp server. I am able to do this using "system" command.
But once connection is done, I need to perform ftp operations like ls, get, put from the C code. I have no idea on how to access ftp shell prompt from C code. Any inputs on this will be of great help.

Thanks in advance,
Srinidhi KV

---

### Post by doobrie on 2012-02-07
> **srinidhi.kv said:**
> Hello All,
           I am writing a C program where I would like to connect to a ftp server. I am able to do this using "system" command.
But once connection is done, I need to perform ftp operations like ls, get, put from the C code. I have no idea on how to access ftp shell prompt from C code. Any inputs on this will be of great help.

Thanks in advance,
Srinidhi KV
With FTP I believe you can specify options to the command line, so you should just be able to execute one long FTP command to upload / download from the server.

---

### Post by ibrahimtawbe on 2012-02-07
go to synaptic or software manager and search for ftplib-dev 
or 
```
apt-cache show ftplib-dev
```
> 
Ftplib makes it easier for C programmers to use file transfer in their
programs.  This package is required to compile and link programs that
use ftplib.  It includes an example command line utility for
transferring files via ftp (RFC959).


---

