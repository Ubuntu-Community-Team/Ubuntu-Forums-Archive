---
title: "FTP programs"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by CouchMaster on 2008-05-07
It seems that I have a few ftp programs installed (Ubuntu 8.04) but I can't find them.  So where are they and how do you run them?

---

### Post by Monicker on 2008-05-07
If they have graphical interfaces, they should be under Applications -> Internet.  If they are command line applications you can go to Applications -> Accessories -> Terminal, and run them from there.

Which ftp programs did you install?

---

### Post by stchman on 2008-05-07
> **CouchMaster said:**
> It seems that I have a few ftp programs installed (Ubuntu 8.04) but I can't find them.  So where are they and how do you run them?

Filezilla is a really nice FTP program.

```
sudo apt-get install filezilla
```

---

### Post by CouchMaster on 2008-05-07
ftp is shown to be installed already - as is lftp
I installed foftp and none show up anywhere.  When I try to run from a terminal I get 'run' command not found.  Perhaps I'm doing it wrong, what is the correct way to run from a term?

---

### Post by t0p on 2008-05-07
Dunno about Hardy, but Gutsy comes with the following ftp programs ready-installed:

**ftp** 
**lftp** 
**netkit-ftp**
**pftp**
**sftp**

As for instructions, check out the relevant man pages (eg. **man ftp**)

Also, there's an add-on for firefox called **FireFTP**, which gives you a nice graphical file transfer app built into the browser.

---

### Post by Monicker on 2008-05-07
Hrmm. I am not familiar with foftp, and I can't seem to find it in the repos, but lftp is there when I run it from a terminal session.
```

lftp ftp.cis.uab.edu

lftp ftp.cis.uab.edu:~> ls                          
drwxr-xr-x    3 0        0              72 Sep 29  2005 pub
```

---

### Post by CouchMaster on 2008-05-07
FileZilla shows up under internet so I'll start learning it - thanks...

---

### Post by justmehere on 2008-05-07
If you just want to connect to a server to transfer files using ftp just use **Connect to Server** on the **Places** menu and choose **Public ftp** or **ftp (with login)** in the Service type. You can then just use standard file browser windows to do your ftp work.

It's often easier to find a complicated answer because we don't look for one that's simple.

---

### Post by bodhi.zazen on 2008-05-07
I like gftp, simple, works

---

### Post by CouchMaster on 2008-05-07
FileZilla with BlueFish seems to be working pretty good.
I was using PSPad and WSFTP Lite - 
BlueFish is almost identical to PSPad
Does linux have a WSFTP clone?

---

### Post by CouchMaster on 2008-05-07
Found it - in case anyone else is curious
gFtp is a very close clone of WSFTP - works almost identically and shows uo in applications.
Thanks

---

