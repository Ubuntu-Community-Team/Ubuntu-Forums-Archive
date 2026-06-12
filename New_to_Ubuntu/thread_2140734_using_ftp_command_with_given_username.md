---
title: "using ftp command with given username?"
date: 2013-04-30
forum: New to Ubuntu
---

### Post by honeybear on 2013-04-30
Hi 

I try : 

$ ftp
open

I enter given url
I enter given username
I enter given password

and error msg:



Password:
230 Welcome to your web hosting account!Please upload your web site inside the directory of the respective hostname.(If you wish to upload outside the hostname directories or delete them please make sure Directory Protection is set to OFF from your hosting control panel - File Manager section)
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> ls
500 Unable to service PORT commands
ftp: bind: Address already in use
ftp> lls
?Invalid command
ftp> dir
500 Unable to service PORT commands
ftp> 

what to do please?
thanks

---

### Post by Lars Noodén on 2013-04-30
You might try [ncftp](http://linux.die.net/man/1/ncftp) instead of plain vanilla ftp.  It allows you to point it at a URL and has some nice shortcuts for anonymous FTP.  You have to install it though.  It's in the repository.

```

ncftp ftp://ftp.eu.openbsd.org/pub/OpenBSD/snapshots/loongson/

```

The package also includes [ncftpget](http://manpages.ubuntu.com/manpages/raring/en/man1/ncftpget.1.html)

Plain FTP requires that you enter a username manually, even if it is 'anonymous'

---

### Post by jonobr on 2013-04-30
Hello

try ftp -p to enter passive mode

---

### Post by honeybear on 2013-05-01
> **jonobr said:**
> Hello

try ftp -p to enter passive mode

thank you so much !!!


passivve worked 

$ ftp -p urlsite

---

### Post by alphacrucis2 on 2013-05-01
If you want a gui ftp program then filezilla is quite good. It's cross platform and is in the universe repo for ubuntu. It supports passive ftp so it should work for you.

---

### Post by oldos2er on 2013-05-01
Doesn't Nautilus support ftp?

---

### Post by alphacrucis2 on 2013-05-01
> **oldos2er said:**
> Doesn't Nautilus support ftp?

It used to. I haven't tried it since the gnome devs did their slash and burn attack on it.

---

