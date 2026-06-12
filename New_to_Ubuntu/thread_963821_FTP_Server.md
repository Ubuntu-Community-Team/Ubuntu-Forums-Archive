---
title: "FTP Server"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ollie123 on 2008-10-30
Hello there, I am totally new to linux. I have set up Ubuntu server editon on my dell dimension 3100. How can I set up an FTP server so the root directory is /var/www? I would appreciate help. Thanks.

[EDIT]: I have heard about a few ftp-servers including vsftpd, pro-ftpd and pure-ftpd. Can you reccomend one of these?

---

### Post by Nepherte on 2008-10-30
I can recommend proftpd: [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588)
It's not hard to setup either.

---

### Post by tomele on 2008-12-02
Hi, I recommend pure-ftpd.
Also I have written a short article on my blog on how to install and configure it : [http://www.ubuntu-howto.info/tag/pure-ftpd]("http://www.ubuntu-howto.info/tag/pure-ftpd")
I like pure ftpd, never had a problem with it, including ssl support.
Hope this helps !

---

### Post by binbash on 2008-12-02
+1 for pure-ftpd

---

### Post by porteclefs on 2008-12-02
+1 for pure-ftp...

i'd point out that ftp is not very secure, so you might want to have a look around and make sure that ftp is the file sharing solution that's right for you.

---

### Post by davidshere on 2008-12-02
Install openssh-server (server) and use SFTP (client).  More secure than ftp.  Avoid telnet and ftp if you can.

Use apache2 (web server) if the people to whom you need to provide files do not also need to upload them to you.  

What is your file sharing situation?  
To whom do you wish to share files?
What is the size of the files?
Are the files shared over the internet or over a private network?  If it's a private network you can use windows file sharing by installing samba on your ubuntu machine.

---

### Post by hyper_ch on 2008-12-02
I'd also go for openssh server... very simple to setup.

---

