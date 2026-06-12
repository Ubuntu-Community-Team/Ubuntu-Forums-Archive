---
title: "Connecting laptop and desktop"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by RicoB on 2008-10-05
Hi! I have a laptop and a desktop, both installed with Ubuntu 8.04, want to connect them by cable and perhaps synchronize some folders and files between them.
Is there any "nice and clean" way to do this? any good tutorial for newbies?

I've installed samba in both computers and shared a folder of my laptop, I could see it (the folder)  on my desktop, but cannot create or remove files (something about permissions), so I only got an "half" solution.

I don't know much about networking and stuff(maybe I should spend some time learning), so I presume there is a simpler and intelligent way to do this. 

 I would appreciate your pointers.

Rico B.

---

### Post by patrickballeux on 2008-10-05
If you don't have any Windows involved in your network, use "OpenSSH Server" for remote access and file sharing.

Samba works OK, but security is a little hard to setup...

Using SSH server makes it easier to access remote terminal and hardrive because your credentials are the same as your local users.

> sudo apt-get install openssh-server

It will install the ssh server and it will work by default.  Simply access your server like this:

Terminal (like telnet) ssh [YOUR_USER]@[YOUR_IP_ADDRESS]
Files access: In Nautilus: ssh://[YOUR_USER]@[YOUR_IP_ADDRESS]/

You will be asked to accept a certificate (click "Accept"). 

No need for Telnet/FTP/Samba, all is provided by SSH, and your connections will be secured also...

As for Samba, you need to create a user mapping between your local users and the "samba users" with the right permissions.

You can try the package : system-config-samba
> sudo apt-get install system-config-samba

It is a GUI that can configure your Samba server for file sharing.

Hope I could helped you...

---

### Post by RicoB on 2008-10-05
Thanks for reply, I will give it a try in the weekend(busy week).
I'll write something as soon as I can.

Thanks.

---

### Post by handydan918 on 2008-10-05
+1    on using ssh. It is really a great tool, and once you have the server part installed, you can also use scp (secure copy) to copy files (or entire directories) across the network.

---

### Post by taladan on 2008-10-05
Not only that, but you can also add the computers host names to your /etc/hosts file with their IP addresses (assuming both computers have a static IP address) so you can connect via the host name.  If you have the same username on each system you can also set up SSH so that you can connect without having to type in your password each time - it does take a little doing, and it /can/ be a security risk if other people use either of these computers on your network, but if you're running a fairly secure network then it shouldn't be an issue.

If you're interested in setting up passwordless ssh authentication, check out [http://www.cneophytou.com/2008/02/05/smooth-ssh-passwordless-authentication/]("http://www.cneophytou.com/2008/02/05/smooth-ssh-passwordless-authentication/")

If you need help on editing your hosts file, just ask ;)

Hope this helps out,

Tal

---

