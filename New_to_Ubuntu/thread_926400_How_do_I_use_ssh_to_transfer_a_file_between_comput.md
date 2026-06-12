---
title: "How do I use ssh to transfer a file between computers on the same network?"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by jon.reeve on 2008-09-21
Hi, I'm relatively new to Linux and I don't know how to use ssh all that well. Man pages are still kind of mystery to me. I'd like to know how to transfer files between two computers on the same home network. I know there's probably a way to do this with ssh, but I'm not sure what that is. Also, I don't know how to check and see what ip addresses each computer has been assigned. Does anyone know the commands for these operations? Thx!

---

### Post by lisati on 2008-09-21
There are several ways of doing this. This commonly involves setting up something like "samba" and shared folders.

You might find the following thread useful for setting things up so that you can see one computer's shared folder on another: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
(Don't be put off by it referring to Windows - much of the information is relevant to Linux-only networks)

---

### Post by willca on 2008-09-23
Hello

A few assumptions.

Ubuntu to Windows and vice-versa but doing the transferring from Windows.
If this is the case, google winscp and use that to connect to your Ubuntu box assuming you got ssh in there.

To verify your Ubuntu has ssh:
$ ssh localhost
If you get a reply as such....then its there...
wanbol@xzbit:/var/cache$ ssh localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is d6:95:c4:ec:e6:89:14:18:ce:13:f9:62:0e:da:84:e3.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'localhost' (RSA) to the list of known hosts.
wanbol@localhost's password:

So now figure your IP.
$ sudo ifconfig eth0

If eth0 is your NIC, otherwise just type sudo ifconfig for the whole long list.

---

