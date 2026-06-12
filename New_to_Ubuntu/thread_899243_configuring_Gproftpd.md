---
title: "configuring Gproftpd"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by quinnten83 on 2008-08-24
Hi
I'm trying to setup an ftp connection to my one of my computers.
The idea is to have an anonymous login so a friend of mine can download some files
on my server. The FTP server does not have to keep running in the background.
I thought I'd start first by testing it out inside my own network and then
later figure out how I can let people connect over the internet.

I downloaded and tried to configure Gproftpd.
I have no idea what the settings mean exactly or what the terminology means, but I managed to configure
it well enough for my windows laptop running Filezilla to connect to my desktop running the gproftp server.
But Filezilla times out everytime stating error Connection timed out, failed to retrieve directory listing.
In gproftp, under the security tab, it says that the logon was successful, but it gives no other reason why the user might have 
been disconnected or why the connection might have timed out.

I don't know if the error is in my configuration or if it is a filezilla thing. 
But in trying to find an instruction or tutorial or even any documentation on Gproftp (at least the frontend) I can hardly find 
anything definitive. Not even a measly gftppro for dummies. even the website of the Gadminstool isn't registred, they use an ip number.

So can anyone help me with this issue?

---

### Post by gmoney on 2008-08-30
Here's a link to a how-to on gproftpd:

[http://ubuntuforums.org/showthread.php?p=429783#post429783](http://ubuntuforums.org/showthread.php?p=429783#post429783)

If you're still having trouble with this application, you may want to uninstall that ftp server, and give vsftpd a shot.  Here's two separate how-to's on vsftpd:

[https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/ftp-server.html)
[http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux](http://www.wikihow.com/Set-up-an-FTP-Server-in-Ubuntu-Linux)

---

