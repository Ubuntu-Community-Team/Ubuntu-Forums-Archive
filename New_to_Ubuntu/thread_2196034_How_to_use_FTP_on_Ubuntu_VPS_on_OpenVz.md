---
title: "How to use FTP on Ubuntu VPS on OpenVz"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by rockcomics on 2013-12-27
Hello everyone! I have no idea what I am doing.

I bought a "Virtual Private Server" on OpenVz from crissic.net. It is running Ubuntu 13.10 x64. My main IP is <removed>
I have no idea how to administer an Ubuntu server. I use Windows 8. I downloaded putty to SSH into my server.

Could someone please explain to me in the simplest of terms how to install an "FTP Daemon" on my server so I can upload files and create my website?

The only reason I bought this Virtual Private Server is to make a website with FTP. This is much harder than I anticipated lol.

Thank you very much!

---

### Post by sandyd on 2013-12-28
please do not post your public ip on a forum, it allows others to access your server

Thanks

---

### Post by CharlesA on 2013-12-28
If you are just using ftp to transfer files, just use sftp instead as it is already included with openssh-server.

I would recommend securing ssh on your server before doing anything else. That way you make sure no one is able to access your machine.

See here:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)

Sidenote, I would only run a LTS release like 12.04 on a production server. A 6 month release cycle is too short for my tastes.

---

