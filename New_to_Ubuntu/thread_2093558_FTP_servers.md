---
title: "FTP servers"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by wiradog on 2012-12-11
Hi
I am setting up a Ubuntu server to act as a NAS, I want to set up a FTP server for a third party to use, who is not used to nux.
SAMBA contains an FTP server in the mix, and I have also looked at Filezilla-can anyone tell me if the GUI connected with the SAMBA ftp server is as user friendly as Filezilla for a non nux person.:D

---

### Post by mastablasta on 2012-12-11
i would go with filezilla i use it to access linux hosting server both from windows and linux. it's a very easy to use and very straightforward GUI.
 
or any NAS GUI solutions such as debian based openmedia vault.

---

### Post by HermanAB on 2012-12-11
No, Samba doesn't really provide FTP.

You should install vsftpd or proftpd.  They both work out of the box.  The only people who have trouble with them are the ones who insist on changing the default settings, before getting familiar with it and reading the manuals.

---

### Post by wiradog on 2012-12-11
Thanks Guys,

You have given me something to think about, at least the SAMBA question is solved-thanks;)

---

