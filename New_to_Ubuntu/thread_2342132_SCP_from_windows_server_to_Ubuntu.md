---
title: "SCP from windows server to Ubuntu"
date: 2016-11-04
forum: New to Ubuntu
---

### Post by arcticmask on 2016-11-04
Dear Everyone,

I'm very new to Ubuntu and integration to windows server. 
My purpose is to copy a file from windows server to Ubuntu while **logged into Ubuntu**,

scp username@<windows server IP>:/path/to/file /path/to/destination
[B]ssh: connect to host <windows server IP> port 22: Connection refused
[/B]

I would need everyone's expertise to tell me what did i miss. Do i need to mount Windows path into Ubuntu? Do i need some kind of ssh server installed on Windows? :confused:

The final purpose of this is to set a **cronjob** that would send files from Windows server to Ubuntu. 

Thanks in advance!

---

### Post by jerome1232 on 2016-11-04
For that to work the Windows server would have to have a running ssh server (not something a windows server typically has). Does it?

---

### Post by kevdog on 2016-11-04
I dont understand -- you want to send files from Windows to Ubuntu -- but then do an ssh from Ubuntu to Windows when logged into Ubuntu??

What you want to do is doable.

What are you using for your ssh client?
You could use scp for this purpose or possibly rsync which can run over ssh (for encryption transport layer).  rsync is well suited for a bunch of file syncs.  Are you using cygwin on windows?

---

### Post by arcticmask on 2016-11-06
Hi, Thanks all for the reply, hope you had a good weekend. 
My purpose is to have a crontab/cronjob running on Ubuntu that can pull files from Windows to Ubuntu on a daily basis. 
[COLOR=#000000]
"Windows server would have to have a running ssh server",[/COLOR] can i use FreeSSHd for this purpose? 
[COLOR=#000000]"rsync is well suited for a bunch of file syncs. Are you using cygwin on windows?"[/COLOR] I'm not familiar with any of these, which one is better for my situation?

Thanks in advance!

Regards,
Robinsen

---

### Post by kevdog on 2016-11-07
Youll need an SSH server setup on the windows machine.  I've only ever used cygwin on Windows to accomplish this, however there are other methods as well.

---

### Post by jerome1232 on 2016-11-07
FreeSSHd should work, I've only ever used openSSH, it's been awhile since I've really messed with Windows. Once you have the ssh server setup on the windows server (I'd suggest you secure it with pgp keys and disable password logins)

Here's a quick guide to getting OpenSSH going.

[https://winscp.net/eng/docs/guide_windows_openssh_server](https://winscp.net/eng/docs/guide_windows_openssh_server)

---

### Post by SeijiSensei on 2016-11-07
Unless you really need these connections to be encrypted, you might find it a lot easier to use smbget, part of the **smbclient** package,  to access a share on the Windows machine.  For details see "[man smbget]("https://www.samba.org/samba/docs/man/manpages/smbget.1.html")".

---

