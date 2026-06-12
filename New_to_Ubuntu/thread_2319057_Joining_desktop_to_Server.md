---
title: "Joining desktop to Server"
date: 2016-03-31
forum: New to Ubuntu
---

### Post by Christian_Smith on 2016-03-31
I'm pretty new to Ubuntu. I figure it has to be possible to connect to the server at my work but so far I haven't been able to find how to do it. 
I know the file server here uses Windows Server 2012 R2. I have a login for the server and I also know the administrator login. I just want to know how to connect ubuntu to the domain so I can view my files on the server. Is this easily done?

---

### Post by SeijiSensei on 2016-04-01
Are you connecting from a machine on the same network as the server?  Trying to connect remotely is pretty difficult without something like a virtual private network.  

If you're on the same network, try typing "smb://servername/" into the address bar in the Nautilus file browser.  You may be prompted for a username and password depending on whether the server requires authentication.  You should see the available shares on the server.

Joining an Active Directory domain is trickier.  Read this: [https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto](https://help.ubuntu.com/community/ActiveDirectoryWinbindHowto)

---

