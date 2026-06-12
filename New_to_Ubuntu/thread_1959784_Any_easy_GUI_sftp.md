---
title: "Any easy GUI sftp?"
date: 2012-04-16
forum: New to Ubuntu
---

### Post by vagelism on 2012-04-16
Hello to all!
I tried to install some sftp but I got lost threw the commands of tutorials and shroot .... I only need to make a directory published threw sftp.
Thank you!

---

### Post by rg4w on 2012-04-16
n/a

---

### Post by perspectoff on 2012-04-16
Filezilla does sftp.

---

### Post by vagelism on 2012-04-16
?

---

### Post by vagelism on 2012-04-16
> **perspectoff said:**
> Filezilla does sftp.

Thank you!

---

### Post by perspectoff on 2012-04-16
OpenSSH has built-in sftp server capabilities. 

If that is what you are trying to do, then that will be the easiest.

You will need to set up OpenSSH to do that.

The other options are to set up either vsftp or proftp ftp servers.

None really have a GUI setup, to my knowledge, but they aren't particularly difficult to set up.

I used the instructions here:

[http://ubuntuguide.org/wiki/FTP_tips](http://ubuntuguide.org/wiki/FTP_tips)

---

### Post by vagelism on 2012-04-16
Thank you! 
I will try it!
The filezilla as I saw is only client version for now on ubuntu and server only on windows. Am I right?

---

### Post by perspectoff on 2012-04-16
You are correct. The Filezilla server still does not seem to be available for Linux.

On their forums, though, they list PureFTPd as an FTP server with a GUI interface. I have not tried that one, though.

GL!

[http://www.pureftpd.org/project/pure-ftpd](http://www.pureftpd.org/project/pure-ftpd)

---

### Post by MBybee on 2012-04-16
Just thought I would point out you can do this directly from Nautilus.

Just go to "File|Connect to server" then pull down "Type".

It even supports hopping through multiple hosts - I use it all the time.

/edit - Sorry, do you mean SSHD (so hosts can connect to *you*) or SSH to connect to hosts?
For SSHD try openssh-server (in the ubuntu software center)

---

### Post by codemaniac on 2012-04-16
+1 for FileZilla .

---

