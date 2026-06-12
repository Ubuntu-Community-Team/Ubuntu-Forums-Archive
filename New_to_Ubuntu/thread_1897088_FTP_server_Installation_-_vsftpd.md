---
title: "FTP server Installation - vsftpd"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by cyclone_ on 2011-12-18
Hi,
Following the instructions in the [ubuntu documentation]("https://help.ubuntu.com/8.04/serverguide/C/ftp-server.html") for how to install vsftpd I get the following error message when I try to start the ftp server (start vsftpd): 

start: Rejected send message, 1 matched rules; type="method_call", sender=":1.79" (uid=1000 pid=21052 comm="start vsftpd ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

All I want is really to have some ftp set up so my wife and I can reach our stationary computer from our laptops. 

I get the feeling from reading this incomprehensible (to me) error message that it has something to do with setting username? I tried:
sudo edit /etc/vsftpd.conf
but that only gave me this error message:

Warning: unknown mime-type for "/etc/vsftpd.conf" -- using "application/octet-stream"
Error: no "edit" mailcap rules found for type "application/octet-stream"

Now I am at a loss, how can I set up this ftp-server?

Thanks

---

### Post by Lars Noodén on 2011-12-18
> **cyclone_ said:**
> All I want is really to have some ftp set up so my wife and I can reach our stationary computer from our laptops.

For that, I would [drop FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/) and use SFTP instead.  To get SFTP up and running, all you have to do is install the package OpenSSH-Server.  No additional configuration is needed.  

Nautilus, Dolphin, and FileZilla are some well-known SFTP clients.

---

### Post by HermanAB on 2011-12-18
Howdy,

The default install of Vsftpd and Proftpd works out of the box.  If it doesn't work, then it is because you tried to 'configure' it...

---

### Post by phyrexia on 2011-12-25
> **HermanAB said:**
> Howdy,

The default install of Vsftpd and Proftpd works out of the box.  If it doesn't work, then it is because you tried to 'configure' it...

respectfully...no, it does not. i have a clean install of 11.10 here and vsftpd is not working properly.  i get a 530 error message when trying to log in with the default .conf file.  can't get it to work after monkeying with it either.

edit: so now it does work with default settings.

---

### Post by Lars Noodén on 2011-12-25
> **phyrexia said:**
> ...can't get it to work after monkeying with it either.

That's why I suggested OpenSSH-Server above to cyclone_  Give it a try.  If it doesn't work out of the box with SFTP, then it is just a few clicks to uninstall.

---

### Post by phyrexia on 2011-12-27
indeed SFTP works straight out of the box.  i did "apt-get purge vsftpd" followed by a "apt-get install vsftpd" and actually, they both work correctly now.  imagine that.  :)

---

### Post by Lars Noodén on 2011-12-27
@phyrexia, you may be interested in reading a bit about FTP vs SFTP:

[http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)

[http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)

---

